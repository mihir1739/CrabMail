# Building an SMTP Server with GNU Mailutils

## Introduction

In this project, we will create a mail server that supports the SMTP (Simple Mail Transfer Protocol) and SASL (Simple Authentication and Security Layer) protocols using the GNU Mailutils library in C++.

## Features

- SMTP server implementation
- SASL protocol support for authentication
- Handling incoming email messages
- Storing and retrieving emails
- User management and authentication

## Prerequisites

- C++ compiler (e.g., GCC, Clang)
- GNU Mailutils library
- CMake (for building the project)

## Getting Started

1. **Clone the repository**:

   ```bash
   git clone https://github.com/your-username/smtp-server.git
   cd smtp-server
   ```

2. **Install the required dependencies**:

   - Install the GNU Mailutils library on your system. The installation process may vary depending on your operating system.
     - On Ubuntu/Debian-based systems:
       ```bash
       sudo apt-get install mailutils
       ```
     - On macOS (using Homebrew):
       ```bash
       brew install mailutils
       ```
     - On Windows, you may need to build the library from source.

3. **Build the project**:

   ```bash
   mkdir build
   cd build
   cmake ..
   make
   ```

4. **Run the SMTP server**:

   ```bash
   ./smtp-server
   ```

   The server will start listening for incoming SMTP connections on the default port (25).

## Usage

1. **Sending an email**:

   You can use a mail client (e.g., Thunderbird, Outlook) or a command-line tool (e.g., `telnet`) to send an email to the SMTP server.

   Example using `telnet`:
   ```
   telnet localhost 25
   HELO example.com
   MAIL FROM:<sender@example.com>
   RCPT TO:<recipient@example.com>
   DATA
   Subject: Test Email
   This is a test email.
   .
   QUIT
   ```

2. **Retrieving emails**:

   The server will store the received emails in a local directory. You can use the GNU Mailutils tools to access and manage the emails.

   Example using `mail`:
   ```
   mail -f /path/to/maildir
   ```

## SASL Protocol Support

The SMTP server supports the SASL protocol for user authentication. To enable SASL, you need to configure the server with user accounts and their credentials.

1. **Configure user accounts**:

   Modify the `users.txt` file in the project directory to add user accounts and their passwords.
   ```
   username1:password1
   username2:password2
   ```

2. **Authenticate with the SMTP server**:

   When sending an email, the mail client should include the SASL authentication credentials.
   ```
   telnet localhost 25
   EHLO example.com
   AUTH LOGIN
   <base64-encoded-username>
   <base64-encoded-password>
   MAIL FROM:<sender@example.com>
   RCPT TO:<recipient@example.com>
   DATA
   Subject: Test Email
   This is a test email.
   .
   QUIT
   ```

## Contributing

Contributions to this project are welcome. If you find any issues or have suggestions for improvements, please feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE). 