<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This is a demonstration of the steps involved in deployment of osTicket, an open-source help desk ticketing system, using Microsoft Azure Virtual Machines. It covers prerequisites, installation, and basic configuration with a two-VM setup including a Domain Controller and Client machine. <br />

<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com/watch?v=LOzmM5ZjKi0) by Tech Hobby

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)

- Remote Desktop Protocol (RDP)

- Internet Information Services (IIS)

- Active Directory Domain Services (ADDS)

- DNS Server

<h2>Operating Systems Used</h2>

- Windows Server 2019 (Domain Controller VM)

- Windows 10 (21H2) (Client VM)

<h2>List of Prerequisites</h2>

- Azure Subscription with sufficient credits (as of this edit on 3/26/25, Microsoft offers $200 trial credit to new users, potentially allowing well over a month's usage of 1-2 VMs.)

- PHP 7.4.x (with required extensions: php-imap, php-gd, php-mbstring)

- MySQL 5.7 or later

- Microsoft IIS 10.0 with CGI module enabled

- osTicket v1.15.4 installation files (download from official site)

- Active Directory domain environment

- Administrative access to both VMs

<h2>Installation Steps</h2>

<h3>Step 1: Provision Azure VMs</h3>
<p>
<a href="https://i.imgur.com/zCppQhb.png" target="_blank">
<img src="https://i.imgur.com/zCppQhb.png" height="80%" width="80%" alt="Azure VM Creation"/>
</a>
</p>
<p>

1. In Azure Portal, create two VMs:
   - "Domain-Controller" (Windows Server 2019)
   - "Client" (Windows 10 21H2)

2. Configure VMs with:
   - Public IP addresses
   - Network Security Group allowing RDP (port 3389)
   - Same Virtual Network for communication

3. Connect via RDP to both machines using their public IPs.
</p>
<br />

<h3>Step 2: Configure Domain Controller</h3>
<p>
<a href="https://i.imgur.com/i1e7OPR.png" target="_blank">
<img src="https://i.imgur.com/i1e7OPR.png" height="80%" width="80%" alt="AD DS Setup"/>
</a>
</p>
<p>

1. Install Active Directory Domain Services role on "Domain-Controller".

2. Promote to Domain Controller with a new forest (e.g., "osticket.local").

3. Configure DNS server settings.

4. Create user accounts for osTicket administration.
</p>
<br />

<h3>Step 3: Install and Configure osTicket on Client VM</h3>
<p>
<a href="https://i.imgur.com/C8FnB5Q.png" target="_blank">
<img src="https://i.imgur.com/C8FnB5Q.png" height="80%" width="80%" alt="osTicket Installation"/>
</a>
</p>
<p>

1. Install IIS with CGI support on "Client" VM.

2. Download and extract osTicket v1.15.4 to C:\inetpub\wwwroot\osticket.

3. Install PHP 7.4 and MySQL 5.7 using Web Platform Installer.

4. Configure PHP extensions in php.ini:
   - enable php_imap.dll, php_gd2.dll, php_mbstring.dll

5. Create a MySQL database and user for osTicket.

6. Run the osTicket installer (http://localhost/osticket/setup):
   - Enter database credentials
   - Set admin username and password

7. Join "Client" VM to the "osticket.local" domain.
</p>
<br />

<h3>Step 4: Test and Create Mock Tickets</h3>


<a href="https://i.imgur.com/q7C52St.jpeg" target="_blank">
<img src="https://i.imgur.com/q7C52St.jpeg" height="80%" width="80%" alt="Mock ticket resolution"/>
</a>

<p>
1. Access osTicket via browser (http://localhost/osticket).

2. Log in as admin and configure:
   - Email settings
   - Ticket queues
   - Agent roles

3. Create and resolve sample tickets to verify functionality.

4. Validate DNS resolution from Domain Controller.
</p>
<br />
