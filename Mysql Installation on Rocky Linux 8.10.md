## Mysql Default Installation

Step 1: Install mysql server

```bash
sudo dnf install mysql-server -y
```
Step 2: Start and Enable the service

```bash
sudo systemctl enable --now mysqld
```
Step 3: Secure the installation
Run the security script to set a root password and remove insecure default settings.

```bash
sudo mysql_secure_installation
```
Step 4: Test the connection
```bash
mysql -u root -p
```
Step 5: (Optional for ease management) Configure .my.cnf file: `/root/.my.cnf` with the following configuration:
```bash
[mysqladmin]
user=root
password=yourpassword

[mysql]
user=root
password=yourpassword

[mysqldump]
user=root
password=yourpassword
```
Step 6: Test the connection again without password
```bash
mysql
```
