# wsl2

> I have installed both Ubuntu and Kali Linux installed at the same time But when I run bash by default it opens up Ubuntu.

In new Windows versions, users can install and run multiple GNU/Linux distributions. One can configure the default distribution (i.e. the distribution that comes up with wsl.exe) with wslconfig /s <disrto_name> command. e.g. To open Kali with wsl.exe at first run, use this command `wslconfig /s kali-linux` or `run kali.exe`.

I have forgotten the `root password` in `Kali`, there is just the terminal of Kali Linux and nothing else. How can I `reset my password` safely?

First of all, I don't know if this procedure is safe or not. At the time of writing, WSL manages the default login user from `DefaultUID` registry (this may change in future). Close any opened WSL instance. To edit this registry value, open Registry Editor or `regedit.exe` from start menu or run dialog box. Go to this registry path or type this path with `Ctrl + L` in that Window:

`HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Lxss` 
You may see one or multiple subkeys (like subfolders) with names something like `{12345678-1234-1234-1234-123456789012} (called GUID)`. Double click on them to open one-by-one and match the DistributionName value with your desired distribution name, here it will be `kali-linux` (see below). Double click on the `DefaultUID` value and change it to `ZERO`. Zero is for root user and `1000 or 0x3e8` (in hexadecimal) for normal users.

Open wsl.exe in command prompt. The prompt changes from `$` to `#` (means root user). Run passwd command in Kali, change root password as usual. Now go back to previous `registry key`, change Zero to previous value (or `3e8` in hex). Here is an example of the registry values:

```
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Lxss]
"DefaultDistribution"="{f029d4cd-b7ee-42bc-ae02-af8f2c97f495}"

[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Lxss\{f029d4cd-b7ee-42bc-ae02-af8f2c97f495}]
"State"=dword:00000001
"DistributionName"="kali-linux"
"Version"=dword:00000001
"BasePath"="C:\\MyFiles\\kali-linux"
"KernelCommandLine"="BOOT_IMAGE=/kernel init=/init ro"
"DefaultUid"=dword:000003e8
"Flags"=dword:00000007
```