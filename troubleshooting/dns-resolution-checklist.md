# Troubleshooting Guide: DNS Resolution Problems

## Purpose

This guide helps diagnose DNS and network connectivity issues on Windows computers.

---

# Step 1 – Check Network Configuration

Open Command Prompt.

Run:

```cmd
ipconfig /all
```

Verify:

- IPv4 Address
- Subnet Mask
- Default Gateway
- Preferred DNS Server

---

# Step 2 – Test Network Connectivity

Ping the gateway.

```cmd
ping 192.168.1.1
```

If the gateway does not respond:

- Check network cable or Wi-Fi
- Verify IP configuration
- Restart the network adapter

---

# Step 3 – Test DNS Resolution

Run:

```cmd
nslookup dc01.corp.local
```

Expected:

The DNS server returns the correct IP address.

---

# Step 4 – Flush the DNS Cache

If DNS is not resolving correctly:

```cmd
ipconfig /flushdns
```

Run the lookup again.

```cmd
nslookup dc01.corp.local
```

---

# Step 5 – Test the DNS Server Directly

```cmd
nslookup dc01.corp.local 192.168.1.10
```

If this works, the client may be using the wrong DNS server.

---

# Step 6 – Reset the Network Stack

If the issue continues:

```cmd
netsh winsock reset
```

```cmd
netsh int ip reset
```

Restart the computer.

---

# Common Problems

| Problem | Possible Cause |
|----------|----------------|
| No Internet | Gateway unavailable |
| DNS lookup fails | Wrong DNS server |
| Can ping IP but not hostname | DNS issue |
| No IP address | DHCP problem |
