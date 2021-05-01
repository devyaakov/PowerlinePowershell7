# Powerline for Powershell 7

Install *PowerShell*
```Powershell
iex "& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI"
```

Install dependencies

```Powershell
Install-Module PANSIES -AllowClobber
```

Install *Powerline*

```Powershell
Install-Module PowerLine
```

## Set Powerline Fonts
Download and Install [Cascadia Code](https://github.com/microsoft/cascadia-code/releases)

Search for the section thats define the settings for the commandline pwsh.exe and set the fontFace property to Cascadia Mono PL on Windows Terminal settings.json:

```Json
"fontFace": "Cascadia Mono PL"
```

## Create Profile

For start the powerline for each **PowerShell** Core session we need to create a profile **Microsoft.PowerShell_profile.ps1** file on the folder ___%USERPROFILE%\Documents\PowerShell\___ with the follow content:

```ps1
Import-Module PowerLine
Set-PowerLinePrompt -PowerLineFont -SetCurrentDirectory -RestoreVirtualTerminal -Colors "#FFDD00", "#FF6600"

[System.Collections.Generic.List[ScriptBlock]]$Prompt = @(
    { "$env:USERNAME 👽" }
    { $executionContext.SessionState.Path.CurrentLocation }
    { '>' * ($nestedPromptLevel + 1) }
)
```
