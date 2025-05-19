# Linux User and Group Management Project
## Project Overview
This project demonstrates how to manage users and groups on a Linux system through the
following tasks:
- Creating users and groups
- Setting up a shared directory with correct permissions
- Applying the SetGID (group sticky bit)
- Enabling collaboration between users
- Granting sudo privileges
## Project Goals
- Create and manage Linux users and groups
- Set up a shared directory with group-based access
- Apply proper file permissions and SetGID
- Switch between users to test collaboration
- Grant and verify sudo permissions
## Step-by-Step Implementation Guide
### 1. Create Two Users
```
sudo adduser alice
sudo adduser bob
```
### 2. Create a New Group
```
sudo groupadd devs
```
### 3. Add Users to the Group
```
sudo usermod -aG devs alice
sudo usermod -aG devs bob
```
### 4. Verify Group Membership
```
groups alice
groups bob
```
### 5. Create the Shared Directory
```
sudo mkdir /opt/devshare
```
### 6. Change Group Ownership
```
sudo chown :devs /opt/devshare
Linux User and Group Management Project
```
### 7. Set Directory Permissions
```
sudo chmod 770 /opt/devshare
```
### 8. Set the SetGID (Group Sticky Bit)
```
sudo chmod g+s /opt/devshare
```
### 9. Test Access as Alice
```
su - alice
cd /opt/devshare
touch alice.txt
ls -l
```
### 10. Test Access as Bob
```
su - bob
cd /opt/devshare
ls -l
nano alice.txt
```
### 11. Grant Sudo Privileges to Alice
```
sudo usermod -aG sudo alice
```
### 12. Verify Sudo Access
```
groups alice
```
## Optional Cleanup
```
sudo deluser alice
sudo deluser bob
sudo groupdel devs
sudo rm -r /opt/devshare
```
