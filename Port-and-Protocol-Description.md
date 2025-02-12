#  Ports and Protocols Guide

### This repository provides a detailed guide to commonly used network ports and protocols across various services, including web servers, control panels, file transfers, remote connections, database systems, and messaging services. Each entry includes the service name, associated port numbers, protocol type (TCP/UDP), and a brief description of its function.

## 1. Application and Web Servers

| No. | Name                        | Port No.                             | Protocol | Description                                                                 |
| --- | --------------------------- | ------------------------------------ | -------- | --------------------------------------------------------------------------- |
| 1   | HTTP                         | 80, 8080, 8081, 8000                | TCP      | Standard protocol for transferring web pages (non-secure).                 |
| 2   | HTTPS                        | 443, 8443, 4443                     | TCP      | Secure version of HTTP, encrypts data between the client and server.        |
| 3   | Tomcat Startup               | 8080                                 | TCP      | Default port for starting Tomcat, a popular Java application server.        |
| 4   | Tomcat Startup (SSL)         | 8443                                 | TCP      | Secure version of Tomcat's startup port using HTTPS.                        |
| 5   | Tomcat Shutdown              | 8005                                 | TCP      | Used to shut down Tomcat server.                                            |
| 6   | Tomcat AJP Connector         | 8009                                 | TCP      | Apache JServ Protocol (AJP) used for communication between web servers.     |
| 7   | GlassFish HTTP               | 8080                                 | TCP      | Default port for the GlassFish Java application server (HTTP).              |
| 8   | GlassFish HTTPS              | 8181                                 | TCP      | Secure version of GlassFish's HTTP service.                                 |
| 9   | GlassFish Admin Server       | 4848                                 | TCP      | Port for accessing the GlassFish admin console.                             |
| 10  | Jetty                        | 8080                                 | TCP      | Web server and servlet container for Java applications.                     |
| 11  | Jonas Admin Console          | 9000                                 | TCP      | Admin console for the Jonas Java EE application server.                     |
| 12  | IHS Administration           | 8008                                 | TCP      | IBM HTTP Server administrative interface.                                   |
| 13  | JBoss Admin Console          | 8080                                 | TCP      | Admin console port for JBoss, an open-source Java EE application server.    |
| 14  | WildFly Admin Console        | 9990                                 | TCP      | Admin console for WildFly, a Java EE application server.                    |
| 15  | WebLogic Admin Console       | 7001                                 | TCP      | Port for accessing Oracle WebLogic Server’s administrative console.        |
| 16  | WAS Admin Console (SSL)      | 9043                                 | TCP      | Admin console for IBM WebSphere, secured with SSL.                          |
| 17  | WAS Admin Console            | 9060                                 | TCP      | Admin console for IBM WebSphere, used for configuring the server.           |
| 18  | WAS JVM HTTP                 | 9080                                 | TCP      | Port for managing Java Virtual Machines (JVM) via WebSphere (HTTP).         |
| 19  | WAS JVM HTTPS                | 9443                                 | TCP      | Secure version of the WebSphere JVM management port.                        |
| 20  | Alfresco Explorer/Share      | 8080                                 | TCP      | Port for Alfresco document management system's web interface.               |
| 21  | Apache Derby Network Server  | 1527                                 | TCP      | Port for Apache Derby, a relational database system, used for client access.|
| 22  | OHS                          | 7777                                 | TCP      | Oracle HTTP Server, used for web server applications.                       |
| 23  | OHS (SSL)                    | 4443                                 | TCP      | Secure Oracle HTTP Server interface.                                        |
| 24  | Jenkins                      | 8080                                 | TCP      | Port for Jenkins, a popular continuous integration tool.                     ---
## 2. Control Panels

| No. | Name                             | Port No. | Protocol | Description                                                                 |
| --- | -------------------------------- | -------- | -------- | --------------------------------------------------------------------------- |
| 1   | cPanel                           | 2082     | TCP      | Control panel for web hosting management (non-secure).                      |
| 2   | cPanel (SSL)                     | 2083     | TCP      | Secure version of cPanel for managing web hosting.                          |
| 3   | WHM                              | 2086     | TCP      | WebHost Manager, used for server administration (non-secure).               |
| 4   | WHM (SSL)                        | 2087     | TCP      | Secure version of WebHost Manager.                                          |
| 5   | Webmail                          | 2095     | TCP      | Access to webmail for email services (non-secure).                          |
| 6   | Webmail (SSL)                    | 2096     | TCP      | Secure version of webmail for accessing email.                             |
| 7   | Plesk Control Panel              | 8880     | TCP      | Control panel for hosting management, similar to cPanel.                    |
| 8   | Plesk Control Panel (SSL)        | 8443     | TCP      | Secure version of Plesk control panel.                                      |
| 9   | Plesk Linux Webmail              | N/A*     | TCP      | Webmail for Plesk (Linux).                                                  |
| 10  | Plesk Windows Webmail (SmarterMail) | 9998**  | TCP      | Webmail for Plesk (Windows), typically SmarterMail interface.               |
| 11  | Virtuozzo                        | 4643     | TCP      | Virtualization platform for managing virtual servers.                       |
| 12  | DotNet Panel                     | 9001     | TCP      | Control panel for .NET hosting management.                                  |
| 13  | DotNet Panel Login               | 80       | TCP      | Login page for DotNet panel (non-secure).                                   |
| 14  | RDP (Remote Desktop Protocol)    | 4489     | TCP      | Used for remote desktop access to Windows servers.                          |
| 15  | SFTP Shared/Reseller Servers     | 2222     | TCP      | Secure File Transfer Protocol, commonly used for file transfers.            |
| 16  | Webdisk                          | 2077     | TCP      | Provides access to a web-based file management system.                      |
| 17  | Webdisk (SSL)                    | 2078     | TCP      | Secure version of Webdisk service.                                          |

## 3. File Transfer

| No. | Name                             | Port No.                                | Protocol | Description                                                                 |
| --- | -------------------------------- | --------------------------------------- | -------- | --------------------------------------------------------------------------- |
| 1   | FTP                              | 21, 20, 2121                           | TCP      | Standard protocol for transferring files between systems (non-secure).     |
| 2   | FTPS                             | 21, 20, 2121, 990, 989                 | TCP      | Secure version of FTP, encrypts the data transfer.                          |
| 3   | RSCP                             | 514                                    | TCP      | Remote System Copy Protocol, used for file transfers in Unix systems.       |
| 4   | OFTP                             | 6619                                   | TCP/UDP  | Odette File Transfer Protocol, used in B2B file transfers.                  |
| 5   | CIFS / SMB / Samba               | 139, 445                               | TCP/UDP  | File-sharing protocol for networked systems (Windows).                      |
| 6   | SSH                              | 22, 2222                               | TCP      | Secure protocol for remote access to servers and file transfers.            |
| 7   | NFS                              | 111, 2049, 4045, 1110                  | TCP      | Network File System, used for sharing files across UNIX/Linux systems.      |
| 8   | TFTP                             | 69                                     | UDP      | Trivial File Transfer Protocol, a simpler version of FTP.                   |
| 9   | HTTP                             | 80, 8080, 8081, 8000                   | TCP      | Standard protocol for web traffic (non-secure).                             |
| 10  | HTTPS                            | 443, 8443, 4443                        | TCP      | Secure version of HTTP, encrypts the data between the client and server.    |
| 11  | Telnet                           | 23                                     | TCP      | An old protocol for accessing remote systems (non-secure).                  |
| 12  | Git                              | 9418                                   | TCP      | Version control protocol used by Git for repositories.                      |
| 13  | Apple Filing Protocol (AFP)     | 548                                    | TCP      | File-sharing protocol for Apple systems.                                    |
| 14  | MooseFS                          | 9419, 9420, 9421, 9422, 9425           | TCP      | Distributed file system protocol, used by MooseFS for large-scale file management. |

## 4. Remote Connection

| No. | Name                             | Port No.         | Protocol | Description                                                                 |
| --- | -------------------------------- | ---------------- | -------- | --------------------------------------------------------------------------- |
| 1   | SSH                              | 22, 2222         | TCP      | Secure protocol for accessing remote systems and managing servers.         |
| 2   | Telnet                           | 23               | TCP      | Unencrypted protocol for remote server access (legacy).                    |
| 3   | RDP (Remote Desktop Protocol)    | 3389             | TCP      | Used to remotely access Windows desktops and servers.                       |
| 4   | VNC                              | 5900, 5902, 5903 | TCP/UDP  | Used for remote desktop control on Linux/Unix systems.                      |

## 5. Directory Access

| No. | Name                             | Port No. | Protocol | Description                                                                 |
| --- | -------------------------------- | -------- | -------- | --------------------------------------------------------------------------- |
| 1   | LDAP                             | 389      | TCP      | Lightweight Directory Access Protocol, used for accessing directory services.|
| 2   | LDAP (SSL)                       | 636      | TCP      | Secure version of LDAP, encrypting the data transfer.                       |

## 6. Databases and Datastores

| No. | Name                             | Port No.  | Protocol | Description                                                                 |
| --- | -------------------------------- | --------- | -------- | --------------------------------------------------------------------------- |
| 1   | DB2                              | 50000     | TCP      | IBM's relational database system.                                           |
| 2   | Redis Servers                    | 6379      | TCP      | In-memory data structure store used as a database, cache, and message broker.|
| 3   | Oracle Listener                  | 1521      | TCP      | Default port for Oracle database connections.                               |
| 4   | MongoDB                          | 27017     | TCP      | Default port for MongoDB, a NoSQL database system.                          |
| 5   | MySQL                            | 3306      | TCP      | Default port for MySQL relational database system.                          |
| 6   | MS SQL                           | 1433      | TCP      | Default port for Microsoft SQL Server database system.                      |
| 7   | Memcached                        | 11211     | TCP      | Distributed memory caching system used for speeding up dynamic web applications.|
| 8   | MariaDB                          | 3306      | TCP      | Open-source relational database system, a MySQL variant.                    |
| 9   | Postgresql                       | 5432      | TCP      | Default port for PostgreSQL, an open-source relational database.            |



### **7. Messaging and Transfer**

| No. | Name                             | Port No.  | Protocol | Description                                                                 |
| --- | -------------------------------- | --------- | -------- | --------------------------------------------------------------------------- |
| 1   | MQ Listener                      | 1414      | TCP/UDP  | Used by IBM MQ for messaging services.                                      |
| 2   | IBM Connect:Direct               | 1364      | TCP/UDP  | File transfer solution for B2B communication.                               |
| 3   | RabbitMQ Web UI                  | 15672     | TCP/UDP  | Web-based interface for RabbitMQ, a messaging broker.                       |
| 4   | Tibco RV Daemon                  | 7474      | TCP/UDP  | Tibco Rendezvous daemon used for messaging in enterprise systems.           |
| 5   | GoToMyPC                         | 8200      | TCP/UDP  | Remote access software for connecting to PCs.                              |



### **8. Mail Transfer**

| No. | Name                             | Port No.  | Protocol | Description                                                                 |
| --- | -------------------------------- | --------- | -------- | --------------------------------------------------------------------------- |
| 1   | POP3                             | 110       | TCP/UDP  | Post Office Protocol, used by email clients to retrieve emails.             |
| 2   | POP3 (SSL)                       | 995       | TCP/UDP  | Secure version of POP3, encrypts email retrieval.                           |
| 3   | IMAP                             | 143       | TCP/UDP  | Internet Message Access Protocol, allows email management on the server.   |
| 4   | IMAP (SSL)                       | 993       | TCP/UDP  | Secure version of IMAP, encrypting email communication.                     |
| 5   | SMTP                             | 25        | TCP/UDP  | Simple Mail Transfer Protocol, used for sending emails.                     |
| 6   | SMTP Alternate                   | 26        | TCP/UDP  | Alternate port for SMTP in case the default (25) is blocked.                |
| 7   | SMTP Alternate                   | 587       | TCP/UDP  | Another alternate port for sending emails securely.                        |
| 8   | SMTP (SSL)                       | 465       | TCP/UDP  | Secure version of SMTP using SSL encryption.                                |

---

### This expanded table includes brief descriptions for each service to help you understand the role of each port and protocol. Let me know if you need further details!
---
by [Tanush Kushwah](https://www.linkedin.com/in/tanush-kushwah-b51a97319/?originalSubdomain=in)
