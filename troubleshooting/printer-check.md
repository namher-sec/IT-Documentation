# Troubleshooting Guide: Network Printer Offline

## Purpose

This guide explains how to troubleshoot a network printer that is offline.

---

# Step 1 – Check the Printer

Verify:

- Printer is powered on
- No paper jam
- No error messages
- Network cable is connected

---

# Step 2 – Test Network Connectivity

Ping the printer.

```cmd
ping 192.168.1.200
```

If the printer does not respond:

- Check the network connection
- Verify the printer IP address
- Restart the printer

---

# Step 3 – Restart the Print Spooler

Open PowerShell as Administrator.

Run:

```powershell
Restart-Service -Name Spooler -Force
```

Try printing again.

---

# Step 4 – Clear the Print Queue

1. Press **Win + R**
2. Type:

```text
services.msc
```

3. Stop **Print Spooler**

Open:

```text
C:\Windows\System32\spool\PRINTERS
```

Delete all files.

Start **Print Spooler** again.

---

# Step 5 – Reconnect the Printer

If the printer is still offline:

- Remove the printer
- Add the printer again
- Install the correct driver
- Print a test page

---

# Verification

Confirm:

- Printer status is **Online**
- Test page prints successfully
- Users can print documents
