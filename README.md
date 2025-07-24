# minitalk

> [!IMPORTANT]
> None of my code is publicly available here, but if you're a recruiter, I'd be happy to share it with you upon request.

<p align="center">
  <img width="317" height="268" alt="Screenshot from 2025-07-23 08-57-06" src="https://github.com/user-attachments/assets/bfae2c73-7a26-403d-acda-06b6cd9f967a" />
</p>

The ***Minitalk*** project is a communication-based assignment at 42 that challenged me to create a simple messaging system between two processes using Unix signals. The goal was to build a server and client in pure C that communicate by encoding characters into binary and transmitting them bit-by-bit through `SIGUSR1` and `SIGUSR2`.
This project deepened my understanding of how inter-process communication can work at a low level, especially in constrained environments where you can't rely on sockets or shared memory.

What I had to do:
* Implement a server program that listens for incoming signals (`SIGUSR1` and `SIGUSR2`)
* Create a client program that sends messages to the server, one character at a time, encoded as binary
* Convert each character into its binary representation and send each bit using signals
* Reconstruct the characters on the server side by catching and assembling incoming bits
* Handle acknowledgments or delays to ensure reliable transmission
  
To achieve this, I had to:
* Master signal handling using `signal()` and `sigaction()`
* Use bitwise operations to encode and decode characters
* Implement safe and synchronous communication between processes
* Handle edge cases like **null terminators**, **special characters**, or **invalid PIDs**

Bonus Part: Advanced Features
* For the bonus part, I expanded Minitalk to:
  * Acknowledge receipt of each character or full message using return signals
  * Handle Unicode characters (multi-byte encoding)
  * Add more robust error handling and checks (e.g., invalid PID, message loss)
  * Support longer messages through signal flow control or queuing

What I Learned:
* The fundamentals of signals and inter-process communication (**IPC**) in Unix
* Bitwise operations and binary encoding/decoding in C
* Writing asynchronous and event-driven code
* Handling race conditions and synchronizing data transmission between processes
* Managing system-level constraints without relying on external libraries

Minitalk was a fun and tricky exercise in low-level communication. It gave me insight into how data can be transmitted using just the operating system's basic features and pushed me to think creatively about timing, precision, and reliability in process-to-process messaging.
