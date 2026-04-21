<p align="center">
  <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo" width="300">
</p>

<h1 align="center">osTicket: Prerequisites and Installation</h1>
This project demonstrates the installation and configuration of osTicket on a Windows 10 virtual machine in Microsoft Azure, focusing on web server setup, dependency management, and database integration.

---

## 🎯 Goals & Objectives

The goal of this project was to install osTicket and understand how web applications depend on services like IIS, PHP, and MySQL.

By the end of this lab, I aimed to:

- Deploy a Windows 10 virtual machine in Azure  
- Install and configure IIS with CGI  
- Install and register PHP with IIS  
- Install and configure MySQL  
- Deploy osTicket into IIS  
- Resolve dependency issues  
- Verify a working ticketing system  

---

## 📌 Overview

In this project, I built a Windows-based environment in Azure to host osTicket. The focus was on configuring required services, resolving setup issues, and validating that the system works end-to-end.

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

- Windows 10 Virtual Machine (`osticket-vm`)  
- IIS with CGI enabled  
- PHP installed in `C:\PHP`  
- MySQL database  
- osTicket deployed in `C:\inetpub\wwwroot\osTicket`  

---

## ⚙️ Implementation

### 1. Virtual Machine Setup
- Created a Windows 10 VM in Azure  
- Connected via Remote Desktop  

<p align="center">
  <img src="images/vm-setup.png" width="700">
</p>

---

### 2. IIS Configuration
- Enabled IIS and CGI to support PHP applications  

<p align="center">
  <img src="images/iis-installation.png" width="700">
</p>

---

### 3. PHP Registration (Problem → Fix)

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

### 4. Dependency Resolution

- Initial setup showed missing PHP extensions  
- Enabled required extensions to proceed  

<p align="center">
  <img src="images/osticket-errors.png" width="700">
</p>

<p align="center">
  <img src="images/osticket-ready.png" width="700">
</p>

---

### 5. MySQL Configuration

- Installed MySQL  
- Verified service was running  
- Created database  

<p align="center">
  <img src="images/mysql-service-running.png" width="700">
</p>

<p align="center">
  <img src="images/heidisql-database.png" width="700">
</p>

---

### 6. osTicket Installation

- Completed installation via browser  

<p align="center">
  <img src="images/osticket-installed.png" width="700">
</p>

- Updated configuration file permissions  

<p align="center">
  <img src="images/cleanup.png" width="700">
</p>

---

### 7. System Validation

- Verified system functionality from both user and admin perspectives  

<p align="center">
  <img src="images/osticket-user-portal.png" width="700">
</p>

<p align="center">
  <img src="images/osticket-staff-panel.png" width="700">
</p>

---

## 🔍 Troubleshooting

### PHP Not Registered
- Problem: IIS could not process PHP  
- Fix: Registered PHP using `php-cgi.exe`  

### Missing Extensions
- Problem: osTicket setup blocked by missing dependencies  
- Fix: Enabled required PHP extensions  

### Database Setup
- Problem: Application required backend database  
- Fix: Installed MySQL and created database  

---

## 📌 Lessons Learned

- Web applications depend on multiple layers (IIS, PHP, database)  
- Misconfiguration is the most common failure point  
- Dependency errors must be resolved before installation  
- Verifying services (like MySQL) is critical  
- Troubleshooting requires isolating one layer at a time  

---

## 💭 Key Takeaways

This project showed that deploying a web application is not just installation—it requires configuring the underlying services correctly.

Most issues came from missing dependencies or configuration gaps, reinforcing the importance of validating each layer before moving forward.
