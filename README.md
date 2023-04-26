# miniedr
miniedr is an antivirus driver. support blocking malware operation.

The list of supported functions is as follows:
1. support blocking "Floxif" virus family.
2. support blocking "Vking" virus family.
3. support blocking "Ramnit" virus family.
4. support blocking process running Judge process ImagePath through regular expression rules.
5. support blocking process running Judge process ComandLine through regular expression rules.
6. support blocking process running by matching program file certificates (sha256).
7. support blocking module loading by matching the certificate of the module file.
8. support for injecting antivirus modules into other processes.

These rules require configuring the registry.
You can refer to the example miniedr.reg.

# miniedr.reg
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\miniedr]
"Type"=dword:00000001
"Start"=dword:00000003
"ErrorControl"=dword:00000001
"ImagePath"=hex(2):5c,00,3f,00,3f,00,5c,00,43,00,3a,00,5c,00,55,00,73,00,65,00,\
  72,00,73,00,5c,00,54,00,68,00,69,00,6e,00,6b,00,70,00,61,00,64,00,5c,00,44,\
  00,65,00,73,00,6b,00,74,00,6f,00,70,00,5c,00,6d,00,69,00,6e,00,69,00,65,00,\
  64,00,72,00,2e,00,73,00,79,00,73,00,00,00
"DisplayName"="miniedr"

### This is the injected module. wow64 process.
"TrampoLib32"="c:\\test\\a32.dll"
### x64 module
"TrampoLib64"="c:\\test\\a64.dll"

### This is a regular example of blocking usage
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\miniedr\ComandLineBlockList]
"xxx"="*4567*"

### This is the sha256 of the digital signature certificate of the file
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\miniedr\Hash]
"a"="c0772d3c9e20c3f4ebb09f5816d6dada0d8fa86563c2d68898539ec1cd355a1b"

### This is a regular example of blocking usage
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\miniedr\ImagePathBlockList]
"1"="*123.exe"

# Extract digital signature certificate from file
### Refer to the document in the cert.zip file.
