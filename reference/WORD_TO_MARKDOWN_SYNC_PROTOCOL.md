# Word Document to Markdown Sync Protocol

## Overview

This protocol documents the process for syncing changes made in Word documents back to the authoritative markdown manuscript. Use this workflow when edits have been made in Word and need to be captured in the markdown source.

---

## File Naming Convention

| File Pattern | Purpose |
|--------------|---------|
| `COMPLETE-MANUSCRIPT-FOR-REVIEW.docx` (with "-") | **Baseline** - Generated from markdown, represents starting point |
| `COMPLETE-MANUSCRIPT_FOR-REVIEW.docx` (with "_") | **Edited** - Contains your manual edits and changes |
| `COMPLETE-MANUSCRIPT-FOR-REVIEW.md` | **Authoritative Source** - The master markdown file to keep in sync |

**Key Rule:** When editing in Word, save a copy changing "-" to "_" in the filename. This preserves the baseline for comparison.

---

## Sync Workflow

### Step 1: Verify File Timeline

Check modification dates to confirm the expected sequence:

```powershell
Get-ChildItem "manuscript\COMPLETE-MANUSCRIPT*" | Select-Object Name, LastWriteTime | Sort-Object LastWriteTime
```

**Expected order:**
1. `-` Word doc (oldest - baseline)
2. `.md` file (middle - may be partially synced)
3. `_` Word doc (newest - contains final edits)

### Step 2: Extract Word Document Text

Extract plain text from both Word documents for comparison:

```powershell
$word = New-Object -ComObject Word.Application
$word.Visible = $false

$doc1 = $word.Documents.Open("full\path\to\COMPLETE-MANUSCRIPT-FOR-REVIEW.docx")
$doc1.Content.Text | Out-File "temp-dash.txt" -Encoding UTF8
$doc1.Close($false)

$doc2 = $word.Documents.Open("full\path\to\COMPLETE-MANUSCRIPT_FOR-REVIEW.docx")
$doc2.Content.Text | Out-File "temp-underscore.txt" -Encoding UTF8
$doc2.Close($false)

$word.Quit()
```

### Step 3: Generate Diff Between Word Versions

Create a diff showing all changes between baseline and edited versions:

```powershell
$dash = Get-Content "temp-dash.txt"
$underscore = Get-Content "temp-underscore.txt"
$diff = Compare-Object $dash $underscore

# Save diff to file
$diff | ForEach-Object { 
    $side = if ($_.SideIndicator -eq '<=') { 'DASH_ONLY' } else { 'UNDERSCORE_ONLY' }
    "$side`t$($_.InputObject)" 
} | Out-File "DIFF-dash-vs-underscore.txt" -Encoding UTF8

Write-Host "Found $($diff.Count) differences"
```

### Step 4: Categorize Changes

For each change identified, check if it exists in the markdown:

| Category | Meaning | Action |
|----------|---------|--------|
| **SYNCED** | Markdown already has underscore version | None needed |
| **NEEDS UPDATE** | Markdown has old dash content | Update markdown |
| **EXCEPTION** | Markdown differs from BOTH versions | User review required |

Use `Select-String` to check for specific phrases:

```powershell
Select-String "phrase to find" "COMPLETE-MANUSCRIPT-FOR-REVIEW.md"
```

### Step 5: Apply Updates

Use find-and-replace to update markdown with underscore content. Include 3-5 lines of context for each replacement to ensure accuracy.

### Step 6: Verify Changes

Spot-check key phrases to confirm updates applied:

```powershell
Select-String "new phrase that should exist" "COMPLETE-MANUSCRIPT-FOR-REVIEW.md"
```

### Step 7: Cleanup

Remove temporary files:

```powershell
Remove-Item "temp-dash.txt", "temp-underscore.txt", "DIFF-*.txt" -ErrorAction SilentlyContinue
```

---

## Exception Handling

When markdown content differs from BOTH Word documents:

1. **Document the exception** - Note what each version says
2. **Flag for user review** - Don't auto-resolve
3. **Get explicit decision** - User chooses which version to use
4. **Apply chosen version** - Update markdown accordingly

---

## Validation Checklist

Before considering sync complete:

- [ ] All UNDERSCORE_ONLY content reflected in markdown
- [ ] All DASH_ONLY content removed/replaced in markdown
- [ ] Exceptions reviewed and resolved
- [ ] Spot-checks pass for key phrases
- [ ] Temp files cleaned up

---

## Quick Reference Commands

```powershell
# Count differences
(Compare-Object (Get-Content "temp-dash.txt") (Get-Content "temp-underscore.txt")).Count

# Check if phrase exists in markdown
Select-String "phrase" "COMPLETE-MANUSCRIPT-FOR-REVIEW.md"

# Check file modification times
Get-ChildItem "COMPLETE-MANUSCRIPT*" | Select Name, LastWriteTime | Sort LastWriteTime
```

---

## Version History

| Date | Notes |
|------|-------|
| 2026-01-24 | Initial protocol created after first sync session |

