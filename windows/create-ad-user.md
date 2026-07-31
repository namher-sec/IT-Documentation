# SOP: Creating a New Active Directory User

## Purpose

This guide explains how to create a new user account in Active Directory Users and Computers (ADUC).

---

## Prerequisites

Before starting, make sure:

- You are signed in with an account that has permission to create users.
- The Domain Controller is available.
- Active Directory Users and Computers (ADUC) is installed.

---

## Step 1 – Open Active Directory Users and Computers

1. Press **Win + R**.
2. Type:

```text
dsa.msc
```

3. Press **Enter**.

---

## Step 2 – Navigate to the Correct Organizational Unit

Open the following location:

```text
corp.local
└── OU_Employees
    └── OU_Marketing
```

Replace the department OU if needed.

---

## Step 3 – Create a New User

1. Right-click the department OU.
2. Select:

```text
New → User
```

3. Enter the user information.

Example:

| Field | Value |
|-------|-------|
| First Name | Max |
| Last Name | Mustermann |
| User Logon Name | mmustermann |

Click **Next**.

---

## Step 4 – Configure the Password

Enter a temporary password.

Recommended options:

- ☑ User must change password at next logon
- ☐ User cannot change password
- ☐ Password never expires
- ☐ Account is disabled

Click **Next**, then **Finish**.

---

# Verification

Check that the new account appears in the correct Organizational Unit.

To verify:

- User is enabled
- Username is correct
- Group memberships are assigned
- User can sign in

---

# Optional

Add the user to security groups.

Example:

```text
Marketing
VPN Users
Office365 Users
Remote Desktop Users
```

Right-click the user → **Properties** → **Member Of** → **Add**.
