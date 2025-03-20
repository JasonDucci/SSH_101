# SSH: Secure Shell Protocol
1. [Overview](#overview)

2. [How does it work](#how)

3. [Uses and Applications](#usage)

4. [Install and Connect SSH](#install)

5. [Conclusion](#conclusion)

<a name="overview"></a>
## 1. Overview
Secure Shell (SSH) is a cryptographic network protocol used to securely access and manage networked devices over an unsecured network. It provides a secure channel between a client and a server, enabling remote command execution, file transfer, and secure tunneling. SSH is widely used in system administration, cloud computing, and secure communications.

SSH was developed as a replacement for Telnet and other insecure remote shell protocols, which transmit credentials and data in plaintext. By leveraging encryption, SSH ensures secure authentication and data transfer, preventing eavesdropping, connection hijacking, and other security threats.

<a name="how"></a>
## 2. How does it work
SSH operates using a client-server model, where an SSH client connects to an SSH server. The connection is encrypted using cryptographic algorithms, ensuring data confidentiality and integrity. SSH typically operates on port 22 by default, though this can be changed for additional security.

### Key Components:

- Authentication: SSH supports various authentication methods, including:

- Password-based authentication (less secure, prone to brute-force attacks)

- Public-key authentication (more secure, uses a key pair: public and private keys)

- Multi-factor authentication (MFA) (adds an extra layer of security)

### Encryption: The protocol employs strong encryption algorithms such as:

- AES (Advanced Encryption Standard) for secure data encryption

- RSA, ECDSA, or Ed25519 for secure key exchange and authentication

- ChaCha20-Poly1305 as an alternative high-performance encryption method

**Secure Tunneling:** SSH can forward ports, allowing secure access to other services through an encrypted channel, such as database connections or web applications.

### Steps of an SSH Connection:

1. The client initiates a connection to the server using an SSH command.

2. The server responds with its public key to establish encryption.

3.The client verifies the server’s identity to prevent Man-in-the-Middle (MitM) attacks.

4. Authentication is performed using a password or key pair.

5. Once authenticated, the user can execute commands or transfer files securely.

<a name="usage"></a>
## 3. Uses and Applications
SSH is a versatile protocol with numerous applications, including:

- Remote Server Administration: System administrators use SSH to securely manage remote servers and devices, performing updates, installations, and troubleshooting.

- File Transfers: Secure Copy Protocol (SCP) and SSH File Transfer Protocol (SFTP) allow secure file transfers between systems.

- Secure Tunneling & Port Forwarding: SSH tunnels encrypt and protect other protocols, such as HTTP, FTP, and database connections. This is useful for securely accessing remote resources over an insecure network.

- Automation and Scripting: SSH is commonly used in automation scripts for deploying applications, managing infrastructure, and running remote commands.

- Git Operations: Many version control systems, including Git, support SSH authentication for secure access to repositories.

- VPN-like Functionality: SSH can act as a lightweight VPN alternative by forwarding traffic securely.

- IoT Device Management: SSH is used to access and manage networked IoT devices securely.

<a name="install"></a>
## 4. Install and Connect SSH

### On Linux/macOS
Most UNIX-based systems come with SSH pre-installed. To check:

```sh 
ssh -V
```
If not installed, use:
```sh 
sudo apt install openssh-client   # Debian-based (Ubuntu)
sudo yum install openssh-clients  # RHEL-based (CentOS)
```
For the SSH server:
```sh 
sudo apt install openssh-server  # Debian-based
sudo systemctl enable --now ssh   # Start SSH service
```
### On Windows:

Windows 10 and later include OpenSSH by default. To install it manually:

Open Settings > Apps > Optional features.

Search for "OpenSSH Client" and "OpenSSH Server", then install.

Start the SSH service using:

Connecting to an SSH Server

To connect to a remote server using SSH:

Example:

If using an SSH key pair:

Generating SSH Key Pairs

To enhance security, SSH key-based authentication is recommended over password authentication. To generate an SSH key pair:

This creates a public and private key pair. The public key should be copied to the remote server using:

Alternatively, you can manually append your public key to the ~/.ssh/authorized_keys file on the server.

Transferring Files via SSH

To securely copy files between a local and remote machine:

To copy an entire directory recursively:

To use SFTP:

SSH Port Forwarding (Tunneling)

Local Port Forwarding

This forwards traffic from a local port to a remote machine securely:

Remote Port Forwarding

This forwards a remote port to a local machine:

Dynamic Port Forwarding (SOCKS Proxy)

This allows SSH to act as a proxy
