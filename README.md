<div id="user-content-toc">
  <ul align="center">
    <summary><h1 style="display: inline-block">👋 Ip addressing and server configuration in ubuntu</h1></summary>
  </ul>
</div>

## DHCP
```bash
   sudo apt install isc-dhcp-server
```
* Default port: 67
### Routes
   - cd /etc/default/
   - cd /etc/dhcp/
   Perform the configuration in the previous routes...
   ```bash
    service isc-dhcp-server restart
   ```
   ```bash
    service isc-dhcp-server status
   ```

## SSH
```bash
sudo apt install openssh-server
```
* Default port: 22
### Routes
   - cd /etc/ssh/
   Perform the configuration in the previous routes...
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
* Default port: 21
### Routes
   ```bash
  sudo gedit /etc/vsftpd.conf
   ```
   - cd /etc
   Perform the configuration in the previous routes...
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
* Default port:  /etc/apache2/ports.conf
### Routes and configuration
   ```bash
	  sudo systemctl start server
   ```
   ```bash
	  sudo systemctl status server
   ```
   ```bash
	  sudo systemctl stop server
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
