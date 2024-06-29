# Winget

## How to update all packages available in Winget?

Use PowerShell with admin privilege, then:

```powershell
winget update --all --source winget --accept-source-agreements --accept-package-agreements --silent
```
