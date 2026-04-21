<p align="center">
  <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo" width="300">
</p>

<h1 align="center">osTicket Deployment on Azure (Windows 10)</h1>

This project demonstrates the deployment of osTicket on a Windows 10 virtual machine in Microsoft Azure, including web server configuration, dependency resolution, and database integration.

---

## 🎯 Goals & Objectives

- Deploy a Windows 10 VM in Azure  
- Configure IIS with CGI support  
- Install and register PHP with IIS  
- Install and configure MySQL  
- Deploy osTicket in IIS  
- Resolve dependency issues  
- Validate full ticketing system functionality  

---

## 📌 Overview

Built a Windows-based hosting environment for osTicket in Azure. The focus was on configuring required services, resolving setup issues, and validating that the application works end-to-end.

---

## 🧰 Technologies Used

- Microsoft Azure (Virtual Machines)  
- Windows 10  
- Remote Desktop Protocol (RDP)  
- Internet Information Services (IIS)  
- PHP  
- MySQL  
- HeidiSQL  
- osTicket  

---

## 💻 Environment

- Windows 10 VM (`osticket-vm`)  
- IIS with CGI enabled  
- PHP installed in `C:\PHP`  
- MySQL database  
- osTicket deployed in `C:\inetpub\wwwroot\osTicket`  

---

## ⚙️ Implementation

### 1. Virtual Machine Setup

- Created and configured a Windows 10 VM in Azure  
- Connected via RDP  

<p align="center">
  <img src="images/vm-setup.png" width="700">
</p>

---

### 2. PHP Configuration (Issue → Resolution)

- IIS initially unable to process PHP  
- Registered PHP using `php-cgi.exe`  

<table align="center">
  <tr>
    <td align="center">
      <img src="images/php-not-registered.png" width="100%"><br>
      <sub>PHP Not Registered</sub>
    </td>
    <td align="center">
      <img src="images/php-registration.png" width="100%"><br>
      <sub>PHP Registered</sub>
    </td>
  </tr>
</table>

---

### 3. MySQL Setup & Database Verification

- Installed MySQL and confirmed service was running  
- Created osTicket database using HeidiSQL  

<p align="center">
  <img src="images/mysql-installation.png" width="700">
</p>

<p align="center">
  <img src="images/heidisql-database.png" width="700">
</p>

---

### 4. osTicket Installation

- Completed installation through browser interface  
- Verified successful deployment  

<p align="center">
  <img src="images/osticket-installed.png" width="700">
</p>

---

### 5. System Validation

- Logged into admin panel  
- Created and verified ticket workflow  

<p align="center">
  <img src="images/osticket-admin-login.png" width="700">
</p>

<p align="center">
  <img src="images/osticket-create-ticket.png" width="700">
</p>

---

## 🔍 Troubleshooting

### PHP Not Registered
- **Problem:** IIS could not execute PHP  
- **Fix:** Registered PHP using FastCGI (`php-cgi.exe`)  

### Dependency Issues
- **Problem:** osTicket installer blocked due to missing PHP components  
- **Fix:** Enabled required PHP extensions  

### Database Setup
- **Problem:** Application required backend database  
- **Fix:** Installed MySQL and configured database via HeidiSQL  

---

## 📌 Lessons Learned

- Web applications rely on multiple layers (IIS, PHP, database)  
- Most failures are configuration-related, not installation-related  
- Dependency validation is critical before deployment  
- Each layer must be tested independently  

---

## 💭 Key Takeaways

Deploying a web application requires proper configuration of underlying services, not just installation.

This project reinforced the importance of troubleshooting systematically and validating each component before moving forward.
