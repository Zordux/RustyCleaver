## Project
Our goal is to explore the fundamentals of Remote Access Trojans (RATs) and experiment with techniques to conceal them within a Windows environment.

## Dropper / Payload Loader
The dropper is responsible for process hollowing svchost.exe to inject our payload into it.

- It will conceal itself and implement a persistence mechanism to ensure the hollowed process remains active, keeping the payload running in the background.

## Payload

The payload serves as the core RAT component, waiting for commands from the C2 server.

- It will execute received commands in the background and send responses back to the C2 server.

## C2 Server
The C2 server facilitates communication with the RAT, issuing commands and receiving execution results.

## Ideas
- DNS-based communication between the C2 server and the client.

- Persistence mechanisms using Registry, Scheduled Tasks, or Windows Services.

- Encryption to protect communication and stored data.

- Obfuscation techniques to evade detection.

## Step-by-Step Breakdown
### 1. Dropper Execution

 1. The dropper is executed on the target machine.

 2. It hides itself and moves to a less suspicious directory (e.g., C:\ProgramData).

 3. It establishes persistence (e.g., adding a Registry key or Scheduled Task).

 4. It uses process hollowing to inject the payload into svchost.exe.

 5. The dropper self-deletes to avoid detection. Detecion off desktop or where ever the user ran it.

### 2. Payload Execution

  1. The payload is now running inside svchost.exe.

  2. It waits for instructions from the C2 server.

  3. It sends an initial beacon to let the server know it's active.

  4. It listens for and executes commands from the C2 server (e.g., file retrieval, keylogging, or system commands).

### 3. C2 Server Communication

  1. The C2 server is set up and listening for incoming connections.

  2. It receives beacons from the infected client.

  3. The attacker sends commands to control the infected machine.

  4. The RAT executes the commands and sends the output back to the server.

## Why Process Hollowing?

Process hollowing is an effective technique because it allows code injection into a trusted system process, making detection more difficult.

- By replacing the memory space of a legitimate process with our own code, we can evade signature-based detection and fingerprinting mechanisms.

- Since execution remains within a recognized system process, this method can help bypass security measures that rely on process integrity verification.
