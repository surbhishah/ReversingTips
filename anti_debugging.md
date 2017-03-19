#Anti debugging techniques

Malware tries to identify if debugger is attached to it and stop executing to prevent analysis.

- Using Windows API functions such as IsDebuggerPresent or NtQueryInformationProcess .

- Using functions like OutputDebugString. This is a function used to send a string to a debugger for display. 

- Manually check process information in PEB Process environment block structure.

- Hide Debugger, HideBug and OhatOm plugins for OllyDbg overcome such checks.

- Identify presence of debugger by scanning own code and seeing if breakpoints have been put. This can be done by scanning 0xCC opcode. 

- Timing checks - code runs slowly if running with a debugger. 

- Timing checks can be performed using rdtsc instruction, GetTickCount() 

- Adding code in TLS callback. Look for .tls section in PE Header. TLS code is executed before hitting the entry point of program and hence is not stopped by the debugger. Debuggers generally break at entry point.

- In IDA Pro, press CTRL-E to display all entry points.

- Change setting in OllyDbg to pause before TLS callback. Options> DebuggingOptions > Events and choose System breakpoint.

- Default setting on most debuggers is to trap exceptions and not pass them to the program. The failure to pass an exception is detected by the process.


- Options > Debugging options > Exceptions setting in OllyDbg

- Malware sometimes tries to exploit vulnerabilities of the debugger itself. For example, OllyDbg evaluates PE header differently than Windows Loader. This can lead to debugger crashing.