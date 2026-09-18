# SS-Utils
### Very often it happens that during a ScreenShare (SS) users disable the clipboard, so that they do not allow us to copy and paste from the SSer's pc to the user's pc, scripts or commands useful for carrying out the SS, for this reason I have created a repository with many scripts that can be useful during an SS, so as to have them all in one place without looking for them everywhere.

# Index

- [Githubs](#Githubs)
- [Services](#Services)
- [BAM](#BAM)
- [Mod Analyzer](#Mod_analyzer)
- [Journal](#Journal)
- [Task Scheduler](#Task-scheduler)
- [Signatures](#Signatures)
- [Alt detector](#Alt-detector)
- [Regex](#Regex)
- [LogFile](#LogFIle)
  
# Githubs

## OrbDIff github

[Orbdiff](https://github.com/orbdiff)

## Spokwn github

[Spokwn](https://github.com/spokwn)

## MeowTonynoh github

[Tonynoh](https://github.com/meowtonynoh)

## Redlotus/Itzicehere github

[Itzicehere](https://github.com/itzicehere)

## Eric zimmerman tools

[Eriz Zimmerman Tools](https://ericzimmerman.github.io/)



# Services

```
powershell "iex(irm 'https://raw.githubusercontent.com/inkenal/rbw-SS-ps/refs/heads/main/Services.ps1')"
```

# BAM

**Redlotus BAM**

```
powershell Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass && powershell Invoke-Expression (Invoke-RestMethod https://raw.githubusercontent.com/PureIntent/ScreenShare/main/RedLotusBam.ps1)
```

**Spokwn BAM PArser**
```
powershell Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass && powershell Invoke-Expression (Invoke-RestMethod https://raw.githubusercontent.com/spokwn/powershells/refs/heads/main/bamparser.ps1)
```
## BAM Deleted Keys
```
powershell Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass && powershell Invoke-Expression (Invoke-RestMethod https://raw.githubusercontent.com/Florinyoq/Screenshare/refs/heads/main/bam.ps1)
```
# Mod_Analyzer

### Habibi Mod Analyzer (by
```
powershell -command "irm 'https://raw.githubusercontent.com/HadronCollision/PowershellScripts/refs/heads/main/HabibiModAnalyzer.ps1' | iex"
```

### Tonynoh Mod Analyzer (by github.com/meowtonynoh)

```
powershell -ExecutionPolicy Bypass -Command "Invoke-Expression (Invoke-RestMethod 'https://raw.githubusercontent.com/MeowTonynoh/MeowModAnalyzer/main/MeowModAnalyzer.ps1')"
```
## JAR

**JAR PArser (by github.com/orbdiff)
```
powershell -command "irm 'https://raw.githubusercontent.com/Orbdiff/JARParser/refs/heads/main/JARParser.ps1' | iex"
```

# Journal

**Cacls**

Cacls is a prefetch bypass method that involves changing the security settings of the ‪C:\Windows\Prefetch folder.
This command shows all security changes that have occurred in the prefetch folder

```
fsutil usn readjournal c: csv | findstr /i /C:"0x00000800" /i /C:"0x80000800" | findstr /i /C:"Prefetch" > Cacls.txt
```
**JnativeHook**

JnativeHook is a string used by autoclickers, when an autoclicker is opened, jnativehook string goes in the %temp% folder.
This command scan the NTFS for JnativeHook flags

```
fsutil usn readjournal c: csv | findstr /i /C:"JnativeHook" | findstr /i /C:".dll" > JnativeHook.txt
```
**Python Executions**

This command scans for all python files executed in the pc (in instance)

```
fsutil usn readjournal C: csv | findstr /i /C:".py" >> PyFilesExecuted.txt
```
**Batch Executions**
This command scans for all batch (.bat) files executed  in the pc (in instance)

```
fsutil usn readjournal C: csv | findstr /i /C:".bat" >> BatFilesExecuted.txt
```
**Prefetch**

This command scans the journal for possible .pf modifications in the ‪C:\Windows\Prefetch folder.

```
fsutil usn readjournal c: csv | findstr /i /C:"0x80000200" /i /C:"0x00001000" /i  /C:"0x00002000" | findstr /i /C:".pf"  > Prefetch.txt
```
**Deleted files**
This command scans the journal for every file deletion of the following extensions:
.exe, .jar, .dll, .pf, .ps1, .py, .bat, JnativeHook

```
fsutil usn readjournal c: csv | findstr /i /C:"0x80000200" | findstr /i /C:".exe" /C:".pf" /C:".jar" /C:".py" /C:".bat" /C:".ps1" /C:"JnativeHook" /C:".dll" > Deleted.txt
```
**Renamed files**

This command scans the journal for every file renames of the following extensions:
.exe, .jar, .dll, .pf, .ps1, .py, .bat, JnativeHook


```
fsutil usn readjournal c: csv | findstr /i /C:"0x00001000" | findstr /i /C:"0x00002000" | findstr /i /C:".exe" /C:".pf" /C:".jar" /C:".py" /C:".bat" /C:".ps1" /C:"JnativeHook" /C:".dll" > Renamed.txt
```
**AHK**
This command scans the journal for every .ahk file modifications

```
fsutil usn readjournal c: csv | findstr /i /C:".ahk" > AHK.txt
```

**ALl files modifcations**
This command scans the journal for every file modifications of the following extensions
.exe, .jar, .dll, .pf, .ps1, .py, .bat, JnativeHook

```
fsutil usn readjournal c: csv | findstr /i /C:"0x80000200" /i /C:"0x00001000" /i  /C:"0x00002000" | findstr /i /C:".pf" /i /C:".exe" /i /C:".bat" /i /C:".cmd" /i /C:".jar" /i /C:".bat" /i /C:".pif" /i /C:"jnativehook" /i /C:"?" > all.txt
```
## Alternate data stream (by github.com/spokwn)
Script that analyze every possible Alternate Data Stream

```
powershell Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass && powershell Invoke-Expression (Invoke-RestMethod https://raw.githubusercontent.com/spokwn/powershells/refs/heads/main/Streams.ps1)
```
## Recording processes (by github.com/orbdiff)
Script that allows you to see every processes that is using GPU and recording the screen, and allows you to kill those processes

```
powershell -command "irm 'https://raw.githubusercontent.com/Orbdiff/powershell/refs/heads/main/kill-screen-processes.ps1' | iex"
```
# Task-Scheduler

**Windows 10/11 Task scheduler**

Script that scans the C:\Windows\System32\Tasks directory 
```
powershell -Command "Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass; Invoke-Expression (Invoke-RestMethod 'https://raw.githubusercontent.com/nolww/project-mohr/refs/heads/main/ManualTasks.ps1')"
```

**Windows Modified Task Scheduler**

Script that scans the C:\Windows\System32\Tasks for OS Modified
```
powershell -Command "Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass; Invoke-Expression (Invoke-RestMethod 'https://raw.githubusercontent.com/ObsessiveBf/Task-Scheduler-Parser/main/script.ps1')"
```
# Signatures 

**Signatures (by github.com/orbdiff)**
```
powershell -command "irm 'https://github.com/Orbdiff/powershell/raw/refs/heads/main/signaturesparser.ps1' | iex"
```
**Signatures (by github.com/spokwn)
```
powershell -command "irm 'https://raw.githubusercontent.com/spokwn/powershells/refs/heads/main/signatures.ps1' | iex"
```
# Alt-Detector
```
powershell Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass && powershell Invoke-Expression (Invoke-RestMethod https://raw.githubusercontent.com/Enr1c0o/Powershell-Scripts/refs/heads/main/Alt-Detector.ps1)
```
also use alt detector by redlotus -> [Itzicehere](https://github.com/itzicehere)

# Regex


## Dll regex
```
^(?:\\\\\?\\)?[A-Za-z]:\\.+$
```
## Exe regex
```
^(?!.*\.dll$)(?:\\\\\?\\)?[A-Za-z]:\\.+$
```

# LogFile

## Log file script
```
powershell -command "Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass; irm 'https://raw.githubusercontent.com/AguaConGas17/Powershells/refs/heads/main/logfileparser.ps1' | iex"
```
