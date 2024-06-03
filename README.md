# Advanced NGINX Hosting with SSL: Multi-Website Configuration

This project demonstrates the process of hosting two separate websites on a single NGINX server. It includes configuring virtual hosts, setting up SSL/TLS for secure communication, and managing multiple websites efficiently.

This project builds upon my previous project, [Advanced Apache Hosting with SSL: Multi-Website Configuration](https://github.com/raoalitalha/apche_multiple_webhost.git), where I initially set up multiple websites on an Apache server. Now, I have expanded it to host multiple websites on NGINX with secure HTTPS connections.

## Project Overview

This project aims to:

- Configure an NGINX server to host multiple websites.
- Set up secure HTTPS connections using self-signed SSL certificates.
- Utilize virtual hosts to manage different websites on a single server.

## Prerequisites

- A machine running a Red Hat-based OS (e.g., CentOS, Fedora).
- Basic knowledge of Linux command-line operations.
- NGINX installed.

## Steps to Achieve the Project

### 1. Checking System Configuration

Ensure you are logged in as the root user and verify the current system settings.

### 2. Installing Necessary Packages

Install and update NGINX and OpenSSL.

### 3. Creating a Self-Signed Certificate

Generate a self-signed SSL certificate to secure your websites.

### 4. Setting Up Directory Structure

Create directories for your websites and download website templates.

### 5. Configuring Virtual Hosts

Set up virtual host configuration files to manage multiple websites.

### 6. Defining IP Address and Domain Names

Update the `/etc/hosts` file to map your domains to your IP address.

### 7. Configuring Log Files

Ensure each website has its own log files for better monitoring and troubleshooting.

### 8. Restarting Services and Configuring Firewall

Restart the NGINX server and configure the firewall to allow HTTP and HTTPS traffic.

### 9. Testing the Websites

Verify that both websites are accessible via the configured domain names.

### 10. Error Handling and Optimization

Configure custom error pages and optimize NGINX settings for better performance.

## Testing the Websites

Open your web browser and navigate to:

- **www.nginxproject.com**

![Screenshot 2024-06-03 100953](https://github.com/raoalitalha/Advanced-NGINX-Hosting/assets/72371702/e6332475-1eba-4c39-832c-a83bb4e9fca1)

- **www.buycars.com**
![Screenshot 2024-06-03 100917](https://github.com/raoalitalha/Advanced-NGINX-Hosting/assets/72371702/3c46f4b9-e9e3-46e6-97c2-cb6e5c73d587)



## Benefits and Learnings

By completing this project, you will:

- Gain experience in setting up and configuring an NGINX server.
- Learn how to manage multiple websites on a single server using virtual hosts.
- Understand how to secure web traffic with SSL/TLS.
- Improve your skills in server administration and web server management.

## Future Plans

In the future, I plan to:

- **Set Up NGINX as a Reverse Proxy**: Implement a reverse proxy setup to balance the load and manage backend services more efficiently.
- **Explore Advanced Load Balancing Techniques**: Utilize NGINX's load balancing features to distribute traffic across multiple servers for improved performance and reliability.

## Conclusion

This project demonstrates how to efficiently host multiple websites on a single NGINX server using virtual hosts and secure them with SSL/TLS. These skills are essential for web developers and system administrators, highlighting your ability to manage web server configurations effectively.
