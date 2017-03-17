#Analyzing Malicious Windows Programs 

####Common Windows API Types

Windows uses Hungarian notation for API function identifiers. So basically, name of argument starts with an identifier that identifies its type. For example - dwSize - dw stand for double word.

Word - w - 16 bit unsigned value
Dword - dw - 32 bit unisgined value
Handles - H - Reference to an object such as a file
Long pointer- LP- LPByte is a pointer to a byte, LPCSTR is a pointer to a character string
Callback - Represents a function that will be called by the WIndows API


####File System functions

CreateFileMapping and MpaViewOfFile

- File can be loaded into memory and manipulated by malware.

- CreateFileMapping function loads a file from disk to memory. 

- MapViewOfFile function returns a pointer to base address of mapping which can be used to access file in memory. 

- FileMappings are commonly used to replicate functionality of loader. After obtaining a map of the file, malware can parse the PE header and make all necessary changes to file in memorythereby causing the PE file to be executed as if it has been loaded by the OS loader. 


####Namespaces

Namespaces can be thought of as a fixed number of folders, each storing different types of objects. The lowest level namespace is NT Namespace \\\.

- Win32 device namespace \\\\.\ is often used by malware to access physical devices directly. 

####Windows Registry

- Early versions of Windows used to use ini files to store configuration information. 

- registry is hierarchical database of config info. 

- Malware often uses registry for persistence or config data. 

- HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run contains a series of values that are executables that are started automatically when user logs in.

####Networking APIs

- Winsock libraries - ws2_32.dll 

- socket: Creates a socket

- bind: Attaches a socket to a port

- listen: Indicates that the socket will be listening for incoming connections

- accept: Opens a connection to a remote socket and accepts the connection

- connect: opens a connection to remote host

- recv : Receives data from remote socket

- send : Sends data to remote socket

- WSAStartup function must be called before any other networking API calls.


####WinINetAPI

High level API - Implements HTTP, FTP etc

####DLLS, Processes and Threads

- Malware often creates a new proces by storing one program insider another in the resource section

- Threat context consists of register values.

####Native API

USERMODE[ User Application -> Kernel32.dll -> Ntdll.dll] -> KERNELMODE[ Ntoskrnl.exe -> Kernel data structures ]

- Some malware may try accessing Ntdll.dll or kernel directly. Non malicious programs do not do this. 


 