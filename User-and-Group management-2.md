# User and Group Management in Linux

A user account in Linux is a record that allows an individual or process to log in and access the system with specific permissions and privileges. It serves as an identity for users to interact with the system, ensuring security and accountability.

## Key Components of a User Account

1. **Username**  
   A unique identifier for the user on the system.  
   Example: `rahul`, `siya`.

2. **User ID (UID)**  
   A unique numerical ID assigned to each user.  
   Example: `0` is reserved for the root user.

3. **Group ID (GID)**  
   Specifies the primary group the user belongs to. Groups help manage permissions collectively.

4. **Home Directory**  
   A personal directory for the user to store files and configuration settings.  
   Example: `/home/username`.

5. **Shell**  
   The default command-line interpreter for the user.  
   Example: `/bin/bash`.

6. **Password**  
   Stored (usually in an encrypted format) to authenticate the user. It is often managed in `/etc/shadow`.

7. **System Files**  
   - **/etc/passwd**: Contains user account information (excluding passwords).  
   - **/etc/shadow**: Stores encrypted password data.

## Types of User Accounts

1. **System Account**  
   Used by system services and processes.  

2. **Regular User Account**  
   Created for individuals to log in and perform tasks.

3. **Service Account**  
   Dedicated accounts for applications or services to run with specific permissions.

## UID and GID Range

1. **UID**:  
   - Regular Users: `1000-60,000`  
   - System Users: `201-999`

2. **GID**:  
   - Regular Groups: `1000-60,000`  
   - System Groups: `201-999`

## Group Management

In Linux, a **group** is a collection of user accounts that share common permissions or privileges. Groups are used to simplify the management of access control by associating permissions with a group rather than individual users.

### Key Features of a Group

1. **Group Name**  
   A unique identifier for the group.  
   Example: `developers`, `admin`.

2. **Group ID (GID)**  
   A unique numerical identifier assigned to each group.

3. **Group Members**  
   A list of users who belong to the group. A user can belong to multiple groups.

4. **Primary Group**  
   Each user is assigned a primary group when their account is created. Files created by the user are associated with this group.

5. **Supplementary Groups**  
   Additional groups a user can be part of for broader permissions.

### Types of Groups

1. **System Groups**  
   Used by system services and processes.  
   Example: `adm`, `daemon`.

2. **User Groups**  
   Created for users to belong to specific roles or teams.

## Benefits of Using Groups

1. **Access Control**  
   Allows collective permission management for files, directories, and resources.

2. **Simplified Administration**  
   Reduces the complexity of managing permissions for multiple users.

3. **Collaboration**  
   Facilitates teamwork by providing shared access to resources.

## Default Permissions

To view the default system configuration and permissions, use the following command:

```bash
cat /etc/login.defs
