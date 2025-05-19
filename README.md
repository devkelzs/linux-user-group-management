Linux User and Group Management Project
 Linux User and Group Management - Detailed Explanation
 Linux User and Group Management Project - Detailed Guide
 Project Goals-------------- Create and manage Linux users and groups.- Set up a shared directory with group-based access.- Apply proper permissions and group sticky bit.- Switch between users to test collaboration.- Grant sudo permissions as needed.
 Step-by-Step Guide-----------------
1. Create Two Users
 $ sudo adduser alice
 $ sudo adduser bob
 Explanation: Creates new users named 'alice' and 'bob'. You'll be prompted to set
 passwords and optional details.
 2. Create a New Group
 $ sudo groupadd devs
 Explanation: Creates a new group called 'devs' which we will use to manage access to a
 shared folder.
 3. Add Users to the Group
 $ sudo usermod -aG devs alice
 $ sudo usermod -aG devs bob
 Explanation: Adds both users to the 'devs' group using the '-aG' flag, which appends
 them to the group without removing existing ones.
 4. Verify Group Membership
 $ groups alice
 $ groups bob
 Explanation: Lists all the groups each user belongs to, confirming they are part of
 'devs'.
 5. Create the Shared Directory
Linux User and Group Management Project
 $ sudo mkdir /opt/devshare
 Explanation: Creates a directory at /opt/devshare where shared files will be stored.
 6. Change Group Ownership
 $ sudo chown :devs /opt/devshare
 Explanation: Changes the group ownership of the folder to 'devs', enabling shared access
 among group members.
 7. Set Permissions
 $ sudo chmod 770 /opt/devshare
 Explanation: Grants full access (read/write/execute) to the owner and group, and no
 access to others.
 8. Set the SetGID (Group Sticky Bit)
 $ sudo chmod g+s /opt/devshare
 Explanation: Ensures all new files created in the directory inherit the group 'devs',
 enforcing collaborative ownership.
 9. Test Access as Alice
 $ su - alice
 $ cd /opt/devshare
 $ touch alice.txt
 $ ls -l
 Explanation: Switch to user 'alice', create a file, and list files to check ownership
 and permissions.
 10. Test Access as Bob
 $ su - bob
 $ cd /opt/devshare
 $ ls -l
 $ nano alice.txt
 Explanation: Switch to 'bob' and confirm he can view and edit the file created by
 'alice'.
 11. Add Alice to sudo Group
 $ sudo usermod -aG sudo alice
 Explanation: Grants 'alice' sudo privileges by adding her to the 'sudo' group.
Linux User and Group Management Project
 12. Verify Sudo Access
 $ groups alice
 Explanation: Ensures 'alice' now has 'sudo' privileges.
 Cleanup (Optional)-----------------
$ sudo deluser alice
 $ sudo deluser bob
 $ sudo groupdel devs
 $ sudo rm -r /opt/devshare
 Explanation: Safely removes the users, group, and shared directory if you want to reset
 the system
