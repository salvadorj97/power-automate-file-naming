# power-automate-file-naming

# Automated File Naming Flow — Power Automate

## Business Problem
Files uploaded to SharePoint were named inconsistently by different team members, 
causing search failures and manual reconciliation work downstream.

## Solution
A Power Automate flow that triggers on file creation, evaluates whether the file 
matches naming targets, and renames it automatically using a standardized 
date-prefix convention — without human intervention.

## Flow Logic
![Flow Diagram](assets/PowerAutomate_Flow.png)

### Key steps:
- **Trigger:** File created in SharePoint (properties only)
- **FileName / LowerName:** Extract and normalize the original filename
- **LoopGuard:** Prevents the flow from triggering on files it already renamed
- **IsTarget:** Conditional check — does this file need renaming?
  - `True` branch: Build `TodayPrefix` + `NewName` + `CleanName` + `SafeName`, 
    then Get file content → Create renamed file → Delete original
  - `False` branch: Skip (1 action — do nothing)

## Impact
- Eliminated manual file renaming across the team
- Standardized naming convention applied automatically on upload
- Zero recurring maintenance required after deployment

## Tools
Power Automate · SharePoint · Microsoft 365
