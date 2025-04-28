# FRAT - Remote Access Tool (Educational Only)

>  ⚠️ **Disclaimer**  
> This project is for **educational purposes only**. Unauthorized or malicious use is strictly prohibited. The authors are **not responsible** for any misuse.

---

## Overview

**FRAT** is a simple Remote Access Tool (RAT) designed to execute basic commands on a client machine.  
It uses **AES encryption** to secure communication and **text files** for command exchange, making it easy to understand and set up.

FRAT does **not** provide administrative privileges or exploit systems. It is intended for educational purposes only.

---

## Features

- Execute shell commands remotely
- AES-encrypted communication
- File-based communication (no networking)
- Basic support for both Windows and Linux commands
- Minimal, easy-to-read C++ codebase

---

## How It Works

FRAT uses two shared text files for communication between the server and the client:

|        File           |                   Purpose                             |
|:----------------------|:------------------------------------------------------|
| `Server - Client.txt` | Server writes encrypted commands for the client       |
| `Client - Server.txt` | Client writes encrypted command output for the server |

Both client and server read, decrypt, and process the contents of these files continuously.

---

## Setup Instructions

1. **Edit File Paths**  
   In both `CLIENT/main.cpp` and `SERVER/main.cpp`, update the paths for:
   - `Client - Server.txt`
   - `Server - Client.txt`
   - `CACHE.txt`
   
2. **Set AES Key (Optional)**  
   Update the `key` array in `AES.cpp` (on both client and server sides) to customize your encryption key.

3. **Compile the Code**  
   Compile using a C++ compiler such as `g++`:
  
   g++ -o client CLIENT/main.cpp CLIENT/AES.cpp
   g++ -o server SERVER/main.cpp SERVER/AES.cpp
  

---

## Supported Commands

### Windows Commands
- `dir` — List files and directories
- `cd [directory]` — Change directory
- `mkdir [directory]` — Create a directory
- `rmdir [directory]` — Remove a directory
- `del [file]` — Delete a file
- `echo [text] > [file]` — Write text to a file
- `type [file]` — Display file contents
- `copy [source] [destination]` — Copy a file
- `move [source] [destination]` — Move or rename a file
- `tasklist` — List running processes
- `taskkill /PID [pid]` — Kill a process by PID

### Linux Commands
- `ls` — List files and directories
- `cd [directory]` — Change directory
- `mkdir [directory]` — Create a directory
- `rmdir [directory]` — Remove a directory
- `rm [file]` — Delete a file
- `echo "[text]" > [file]` — Write text to a file
- `cat [file]` — Display file contents
- `cp [source] [destination]` — Copy a file
- `mv [source] [destination]` — Move or rename a file
- `ps` — List running processes
- `kill [pid]` — Kill a process by PID

---

## Project Structure

```
FRAT/
├── Client - Server.txt         # Client to server communication file
├── Server - Client.txt         # Server to client communication file
├── README.md                   # Project documentation
├── CLIENT/
│   ├── AES.cpp                 # AES encryption implementation
│   ├── AES.h                   # AES encryption header
│   ├── CACHE.txt               # Cache file for client
│   └── main.cpp                # Client logic
├── SERVER/
│   ├── AES.cpp                 # AES encryption implementation
│   ├── AES.h                   # AES encryption header
│   ├── CACHE.txt               # Cache file for server
│   └── main.cpp                # Server logic
```

---

## Final Notes

- FRAT is **not** intended for production use.
- Always obtain **proper authorization** before using FRAT on any machine.
- Use responsibly.

---
