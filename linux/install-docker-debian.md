# SOP: Installing Docker Engine on Debian 12

## Purpose

This guide explains how to install Docker Engine on Debian 12 (Bookworm).

---

## Prerequisites

- Debian 12 installed
- Internet connection
- User with sudo permissions

---

## Step 1 – Update the System

```bash
sudo apt update
sudo apt upgrade -y
```

---

## Step 2 – Install Required Packages

```bash
sudo apt install -y ca-certificates curl gnupg
```

---

## Step 3 – Add Docker Repository

Create the keyring directory.

```bash
sudo install -m 0755 -d /etc/apt/keyrings
```

Download the Docker GPG key.

```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | \
sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

Give the key the correct permissions.

```bash
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

Add the Docker repository.

```bash
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/debian \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

---

## Step 4 – Install Docker

```bash
sudo apt update
```

```bash
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

---

## Step 5 – Verify Installation

Check the Docker service.

```bash
sudo systemctl status docker
```

Run the test container.

```bash
sudo docker run hello-world
```

Expected result:

```text
Hello from Docker!
```

---

# Optional

Allow your user to run Docker without sudo.

```bash
sudo usermod -aG docker $USER
```

Log out and log in again.

Verify:

```bash
docker ps
```
