
# OS TICKET 101

Links:
osTicket Installation Files: https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6


## Part 1 (Create Virtual Machine in Azure)

-  Create a Resource Group

-  Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs

      a. When creating the VM, allow it to create a new Virtual Network (Vnet)

## Part 2 (Installation)

### **Note: These steps are just installing a bunch of prerequisite software and doing it on your own as i did, you can use it as a guide to see how this was done and gain an understanding in the event that you don't understand it already.**



### Create an Azure Virtual Machine Windows 10, 4 vCPUs

-  Name: Vm-osticket
-  Username: labuser (for example/whatever you chose)
-  Password: osTicketPassword1! (for example/whatever you chose)



### Open this: [Installation Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)

-  We will use these files to install osTicket and some of the dependencies. I’m using this offline version to make sure everyone is using the same version of all the files :)

### Install / Enable IIS in Windows WITH CGI and Common HTTP Features

-  World Wide Web Services -> Application Development Features ->

    [X] CGI

    [X] Common HTTP Features

### From the [Installation Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6), download and install [PHP Manager for IIS](https://drive.google.com/file/d/1RHsNd4eWIOwaNpj3JW4vzzmzNUH86wY_/view?usp=share_link) (PHPManagerForIIS_V1.5.0.msi)

### From the [Installation Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6), download and install the [Rewrite Module](https://drive.google.com/file/d/1tIK9GZBKj1JyUP87eewxgdNqn9pZmVmY/view?usp=share_link) (rewrite_amd64_en-US.msi)

### Create the directory C:\PHP

### From the [Installation Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6), download [PHP 7.3.8](https://drive.google.com/file/d/1snNMtLdCOpMtkCyD4mvl9yOOmvVIp9fP/view?usp=share_link) (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP

### **!! ATTENTION !!**

### **If this appears, choose to “Keep” the file:**

<p>
<img src =https://i.imgur.com/knHUqjl.png)
</p>

<p>
<img src =https://i.imgur.com/DRTi05y.png)
</p>
  
### **If you are still having trouble downloading PHP 7.3.8, please try downloading and installing [Google Chrome](https://www.google.com/chrome/) and doing it from within there.** 

### From the [Installation Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6), download and install [VC_redist.x86.exe.](https://drive.google.com/file/d/1s1OsGF3-ioO0_9LYizPRiVuIkb3lFJgH/view?usp=share_link)

### From the [Installation Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6), download and install [MySQL 5.5.62](https://drive.google.com/file/d/1_OWh9p7VQLcrB0q_V7qT8yHl0xo5gv7z/view?usp=share_link) (mysql-5.5.62-win32.msi)

-  Typical Setup ->

-  Launch Configuration Wizard (after install) ->

-  Standard Configuration ->

-  Password1

### Open IIS as an Admin

### Register PHP from within IIS

### Reload IIS (Open IIS, Stop and Start the server)

### Install osTicket v1.15.8

-  Download osTicket from the Installation Files Folder

-  Extract and copy “upload” folder to c:\inetpub\wwwroot

-  Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

### Reload IIS (Open IIS, Stop and Start the server)

### Go to sites -> Default -> osTicket

-  On the right, click “Browse *:80”

### Note that some extensions are not enabled

-  Go back to IIS, sites -> Default -> osTicket

-  Double-click PHP Manager

-  Click “Enable or disable an extension”

    -  Enable: php_imap.dll

    - Enable: php_intl.dll

    - Enable: php_opcache.dll

-  Refresh the osTicket site in your browse, observe the changes

### Rename: ost-config.php

-  From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php

-  To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

### Assign Permissions: ost-config.php

-  Disable inheritance -> Remove All

-  New Permissions -> Everyone -> All

### Continue Setting up osTicket in the browser (click Continue)

-  Name Helpdesk

-  Default email (receives email from customers)

### From the [Installation Files](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6), download and install [HeidiSQL.](https://docs.google.com/document/d/1WovrX2DaS9xkfaSr4LXyB4YnnWpXIgPCMMbbfgHmGVw/edit)

-  Open Heidi SQL

-  Create a new session, root/Password1

-  Connect to the session

-  Create a database called “osTicket”

### Continue Setting up osticket in the browser

-  MySQL Database: osTicket

-  MySQL Username: root

-  MySQL Password: Password1

-  Click “Install Now!”


# Congratulations, hopefully it is installed with no errors!! Now we can use it.

-  Browse to your help desk login page: http://localhost/osTicket/scp/login.php

### End Users osTicket URL:

-  [http://localhost/osTicket/](http://localhost/osTicket/) 

### Clean up

-  Delete: C:\inetpub\wwwroot\osTicket\setup

-  Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php

**Notes:**

*  Browse to your help desk login page: [http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php)

*  End Users osTicket URL: [http://localhost/osTicket/](http://localhost/osTicket/)

## Part 3 (Post Installation Setup)

### Configure [Roles](https://docs.osticket.com/en/latest/Admin/Agents/Roles.html)
 
-  Admin Panel -> Agents -> Roles

-  Supreme Admin

### Configure [Departments](https://docs.osticket.com/en/latest/Admin/Agents/Departments.html)

-  Admin Panel -> Agents -> Departments
  
-  System Administrators

### Configure [Teams](https://docs.osticket.com/en/latest/Admin/Agents/Teams.html)

-  Admin Panel -> Agents -> Teams

   1.  Level I Support
   2.  Level II Support

### Allow anyone to create tickets

-  Admin Panel -> Settings -> User Settings

-  Registration Required: Require registration and login to create tickets

### Configure [Agents](https://docs.osticket.com/en/latest/Admin/Agents/Agents.html) (workers)

-  Admin Panel -> Agents -> Add New

    1. Jane
    2. John

### Configure [Users](https://docs.osticket.com/en/latest/Agent/Users/User%20Directory.html) (customers)

-  Agent Panel -> Users -> Add New

    1. Karen
    2. Ken

### Configure [SLA](https://docs.osticket.com/en/latest/Admin/Manage/SLA%20Plans.html)

-  Admin Panel -> Manage -> SLA

    1. Sev-A (1 hour, 24/7)
    2. Sev-B (4 hours, 24/7)
    3. Sev-C (8 hours, business hours)

### Configure Help Topics

-  Admin Panel -> Manage -> Help Topics

   1. Business Critical Outage
   2. Personal Computer Issues
   3. Equipment Request
   4. Password Reset

## Part 4 (Tickets and Ticket Lifecycle)

### Just practice creating, triaging, and solving tickets.

**-  Ticket examples:**

    1. Sev-A (1 hour, 24/7) [entire mobile/online banking system is down] -> SysAdmins
    2. Sev-B (4 hours, 24/7) [accounting department needs adobe upgrade, broken]
    3. Sev-B/C (2 hours, business hours) [CFO’s laptop seems a bit slow]
  
