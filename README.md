
Certainly! Below is the README file for your assignment, formatted for GitHub:

```markdown
# Chatting Server and Client Program

## Overview

This project involves the development of a chatting server (`chat.ndm.lk`) and client program using the C programming language. The server is designed to be concurrent, handle multiple clients, and includes user registration and chat functionalities.

## Features

### Server

- **Concurrent Server**: Capable of handling multiple clients simultaneously without creating zombie processes.
- **User Registration**: Clients must register themselves with a username and password.
- **One-to-One Chat**: Clients can chat with one other selected client.
- **Waiting Room**: Clients are placed in a waiting room if no other clients are available to chat.
- **DNS Records**: The server has its own DNS record in the DNS server with both forward lookup and reverse lookup zones.
- **Port**: The server listens on port 6001.

### Client

- **User Registration**: Register with the server using a username and password.
- **Chat Functionality**: Chat with an available selected client.
- **Port**: Clients connect using port 6002.

## Prerequisites

- **DSN Service**: Ensure DNS service is set up.
- **Zone Files**: Create Forward lookup zone and Reverse lookup zone.
zone"ns" IN {
type master;
file "forward.ndm.lk";
allow-update { none; };
};

zone"1.0.10.in-addr.arpa" IN {
type master;
file "reverse.ndm.lk";
allow-update { none; };
};

## Assignment Guidelines

1. **Server Requirements**:
    - Create a concurrent server to handle multiple clients.
    - Manage user registrations with passwords.
    - Implement a waiting room for clients when no other clients are available to chat.
    - Use port number 6001 for the server.

2. **Client Requirements**:
    - Register with the server and connect to chat.
    - Use port number 6002 for the client.

3. **DNS Setup**:
    - Ensure the server has a DNS record with forward and reverse lookup zones.

## Installation and Configuration

### Server Setup

1. **Install Necessary Packages**:
    ```bash
    sudo yum install gcc
    sudo yum install bind-utils
    ```

2. **Compile Server Code**:
    ```bash
    gcc -o chat_server chat_server.c -lpthread
    ```

3. **Run the Server**:
    ```bash
    ./chat_server
    ```

### Client Setup

1. **Install Necessary Packages**:
    ```bash
    sudo yum install gcc
    ```

2. **Compile Client Code**:
    ```bash
    gcc -o chat_client chat_client.c
    ```

3. **Run the Client**:
    ```bash
    ./chat_client
    ```

## DNS Configuration

1. **Forward Lookup Zone**:
    - Configure the DNS server to include an entry for `chat.ndm.lk`.
$TTL 86400
@ IN SOA mlb-dc1-centos7.ndm.lk. root.ndm.lk. (
2011071001 ;Serial
3600 ;Refresh
1800 ; Retry
604800 ; Expire
86400 ) ;Minimum TTL
@ IN NS mlb-dc1-centos7.ndm.lk.
@ IN A 10.0.1.2 
@ IN A 10.0.1.3 
mlb-dc1-centos7 IN A 10.0.1.2 
ndm-cli-fedora28 IN A 10.0.1.3


2. **Reverse Lookup Zone**:
    - Configure the DNS server to include the reverse lookup zone for the server IP address.
 $TTL 86400
@ IN SOA mlb-dc1-centos7.ndm.lk. root.ndm.lk. (
2011071001 ;Serial
3600 ;Refresh
1800 ; Retry
604800 ; Expire
86400 ) ;Minimum TTL

@ IN NS mlb-dc1-centos7.ndm.lk.
@ IN PTR csa.lk.
mlb-dc1-centos7 IN A 10.0.1.2 
ndm-cli-fedora28 IN A 10.0.1.3 
2 IN PTR mlb-dc1-centos7.ndm.lk.
3 IN PTR ndm-cli-fedora28.ndm.lk.

## Troubleshooting and Debugging

- Ensure that the DNS records are correctly configured and resolvable.
- Verify that the server and client ports (6001 and 6002) are open and not blocked by a firewall.
- Use logging within the C code to track client connections and communications.

## Report

- Compile a detailed report including all steps, concepts, troubleshooting, and debugging mechanisms.
- Include screenshots of all configurations and steps.
- Use the provided cover page template from CourseWeb.

## Demonstration Guidelines

- **Setup**: Use at least 1 CentOS server and 1-2 clients (preferably virtual machines using VMware or Oracle VB).
- **Demo Requirements**:
    - Connect two clients to the server and demonstrate a chat session.
    - Show the waiting room functionality.
    - Demonstrate DNS resolution for the chat server.

## Viva Session

- Be prepared to demonstrate and explain your configuration and code.
- Stick to the allocated time slot for your viva session.

## Screenshots





