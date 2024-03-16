<div id="user-content-toc">
  <ul align="center">
    <summary><h1 style="display: inline-block">👋 Ip addressing and server configuration in ubuntu</h1></summary>
  </ul>
</div>

## DHCP
```bash
   sudo apt install isc-dhcp-server
```
### Routes
* Default port: 67
   - cd /etc/default/
   - cd /etc/dhcp/
   Perform the configuration in the previous routes...
   - File configuration: "dhcpd.conf"
   ```bash
    service isc-dhcp-server restart 
   ```
   ```bash
    service isc-dhcp-server status
   ```
  https://infotips.es/redes/servidor-dhcp-en-ubuntu-server-22-04-lts/

## SSH
```bash
sudo apt install openssh-server
```
### Routes
* Default port: 22
   - cd /etc/ssh/
   Perform the configuration in the previous routes...
  - Port change: file "sshd_config"
   ```bash
  sudo systemctl start ssh
   ```
   ```bash
  sudo systemctl status ssh
   ```

## FTP
```bash
sudo apt-get install vsftpd
```
### Routes
* Default port: 21
   Perform the configuration in the previous routes...
   - Port change: /etc/vsftpd.conf -> listen_port=21
   ```bash
   sudo gedit /etc/vsftpd.conf
   ```
   Init, restart, status...
   ```bash
   sudo init.d/vsftpd restart
   ```
   ```bash
   sudo init.d/vsftpd start
   ```

## APACHE2
```bash
   sudo apt install apache2
```
* Default port: Listen 80
* Port change: /etc/apache2/ports.conf
### Port configuration and reboot
   ```bash
   sudo gedit /etc/apache2/ports.conf
   ```
   Create or modify an Apache VirtualHost :
   ```bash
   sudo gedit /etc/apache2/sites-enabled
   ```
   Change the port of your preference
   File: "000-default.conf" or other files "example.conf"
   
   Allow Apache to bind to the new port
   ```bash
   sudo systemctl restart apache2
   ```
   ```bash
   sudo netstat -tlpn| grep apache
   ```
   ```bash
   sudo ss -tlpn| grep apache
   ```
   Now, to check that the connection is correct, we will access it from a browser using the following syntax:
   ```bash
   http://Direccion_IP:8081
   ```
### Configuration and status
   ```bash
	  sudo systemctl start apache2
   ```
   ```bash
	  sudo systemctl status apache2
   ```
   ```bash
	  sudo systemctl stop apache2
   ```
### Permissions
   * Routes htmls: cd /var/www/html/

   Read write and execute for all users (not recommendable)
   ```bash
	  sudo chmod 777 /var/www/html/
   ```
   Read write and execute only for the file owner (recommendable)
   ```bash
	  sudo chmod 755 /var/www/html/
   ```
   For individual files the owner has read write and execute permission
   ```bash
	  sudo chmod 664 /var/www/html/index.html
   ```

## Cration and deletion of users
```bash
sudo su
```
    
Create new user with "name-user"
```bash
adduser name-user
```
    
Give administrator permissions
```bash
adduser name-user sudo
```
    
SSH permisions with an IP
```bash
 ssh name-user@0.0.0.0
```
    
Delete user
```bash
 sudo userdel -r name-user
```
