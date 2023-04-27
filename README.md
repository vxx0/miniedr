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

# These rules require configuring the registry.
Refer to the document in the __miniedr.reg__(https://github.com/vxx0/miniedr/blob/main/miniedr.reg).


# Extract digital signature certificate from file.
Refer to the document in the __cert.zip__(https://github.com/vxx0/miniedr/blob/main/cert.zip).

# For other questions. please write Issues.
