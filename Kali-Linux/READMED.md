# How to Install WSL2 on Windows 10

- Step 1. Check the Latest Version of Windows

Type command on Command Prompt or Run Box
`winver`

- Step 2. Enable WSL2 on Windows

To enable WSL2, Press the Windows start key and search for Powershell and Click on Run as Administrator and allow UAC control to Yes.

Type or copy-paste the following command on Windows PowerShell
`dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart`

Now restart your machine.

- Step 3. Set WSL version to WSL2

Again, start Powershell as Administrator and type command.

`wsl --set-default-version 2`


Install and Run Kali Linux on WSL2
To Install: open Microsoft Store, press Start Key ,and Search Microsoft Store, or simply click the link below.
https://hackernoon.com/a-short-guide-to-installing-wsl2-and-kali-linux-on-windows-10-p52w310n