# Project Outline and Ideas

Our project goal is to learn the basics of Remote Access Trojans and try to make it hidden in a windows environment.

## Ideas and Features
- C2 server
- Idea: Shows which pc's are online 
<br /> <br />
- Payload 
- Main: No windows api only direct sys calls ? Rust and sys calls dont get along so might have to update to api calls
- First Step: Coding the Dropper
- Second Step: Dropper Stores new exe in a hidden location
- Third Step: Create a Suspended Process for process hollowing
- Forth Step: Write the Payload into suspended process's memory
- Fifth Step: Persistence Registrys? Scheduled task? Windows Services?
- Sixth Step: Test Rat functionality
<br /> <br />
## Why only system calls and why dont system calls seem to be the best method
Useing windows api would most likey be more detectable because they are commanly used in many well known other malware increasing our detection rate.
Rust doesn’t have native, built-in support for system calls unlike C or C++ does. We could use Third-party crates like libc or winapi, but it requires more setup and unsafe code.
So while using sys call might be harder and could lead to more complex code, it would be our best bet to have a worse detection rate.
## Why Process Hollowing
Injecting code into a process that is already verified to be safe is an effective method because all we need to do is ensure that our code is unique and not easily detected, allowing us to bypass fingerprint scans. This is because process hollowing involves taking the original process's code and replacing it with ours, all within memory.
