# SOP: Joining a Windows 11 Computer to Active Directory

## Purpose

This guide explains how to join a Windows 11 computer to an Active Directory domain (`corp.local`).

---

## Prerequisites

Before starting, make sure:

- The Windows 11 computer is connected to the local network.
- The DNS server points to the Domain Controller (`192.168.1.10`).
- You have a Domain Administrator account.
- The Domain Controller is online.

---

## Step 1 – Check Network Connection

Open **PowerShell** as Administrator and run:

```powershell
Test-NetConnection -ComputerName "corp.local" -Port 53
```

### Expected Result

```text
TcpTestSucceeded : True
```

If the test fails, check the network connection and DNS settings before continuing.

---

## Step 2 – Open Computer Name Settings

1. Press **Win + R**
2. Type:

```text
sysdm.cpl
```

3. Press **Enter**.
4. Open the **Computer Name** tab.
5. Click **Change...**

---

## Step 3 – Join the Domain

1. Select **Domain**.
2. Enter:

```text
corp.local
```

3. Click **OK**.

---

## Step 4 – Enter Administrator Credentials

When prompted, enter the domain administrator credentials.

Example:

```text
Username: CORP\DomainAdmin
Password: ********
```

If successful, Windows displays the message:

```text
Welcome to the corp.local domain.
```

Click **OK**.

---

## Step 5 – Restart the Computer

Restart the computer to complete the domain join.

Using PowerShell:

```powershell
Restart-Computer -Force
```

Or restart using the Windows Start menu.

---

# Verification

After the restart:

1. Log in with a domain user account.

Example:

```text
CORP\username
```

2. Open **Command Prompt**.

3. Run:

```cmd
whoami
```

### Expected Output

```text
CORP\username
```

You can also verify the domain membership by opening **System Properties** (`sysdm.cpl`) and checking that the computer belongs to **corp.local**.

---

# Troubleshooting

## Unable to Find the Domain

Check that:

- The DNS server is set to the Domain Controller.
- The Domain Controller is online.
- The client can ping the Domain Controller.

Useful commands:

```powershell
ipconfig /all
```

```powershell
ping corp.local
```

---

## Incorrect Username or Password

- Verify the administrator credentials.
- Make sure the account has permission to join computers to the domain.

---

## Time Synchronization Error

If the system time differs significantly from the Domain Controller, Kerberos authentication may fail.

Check the current time:

```powershell
Get-Date
```

Synchronize the time if necessary.

---

# Result

The Windows 11 computer is now joined to the Active Directory domain (`corp.local`) and users can sign in with their domain accounts.
