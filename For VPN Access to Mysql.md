# Creating Mysql/MariaDB Account for User Accessing Through VPN
For this scenario, it is reccomended to create user as localhost since the vpn will have dhcp ip that will change freqeuntly.
The user will also need ssh port 22 to be open to access the database server.

## 1. Create OS User
```bash
#for rhel/rocky linux
useradd abu
passwd abu
usermod -aG dev abu #developer group
```

## 2. Create Mysql User
```bash
mysql -u root -p
mysql> create user 'abu'@'locathost' identified by 'password';
mysql> grant all privileges on student.* to 'abu'@'localhost';
mysql> flush privileges;
```
## 3. User (The developer) access to databases
a. __In the SSH Tab (The "Bridge")SSH Host / IP__: This must be the IP address of the database server (the EC2 instance, VPS, or physical server) that holds the database.

__SSH User/Password/Key__: The credentials you use to log into the server itself the OS user we created before (e.g., ubuntu, root).


b. __In the Main Database Connection Tab (The "Destination")
Server Host__: This is where you should usually use localhost (or 127.0.0.1).

## 4. Reasons
Why do you use localhost for the Database Host?
Because of how the SSH tunnel works. Once DBeaver successfully connects to your remote server via SSH, DBeaver is 
contextually "inside" that server. From the perspective of the SSH session, the database is running right there on the same machine, which is why localhost works.

Using localhost here is also highly secure because it means your MySQL/MariaDB configuration (bind-address) only needs to listen to local traffic,
keeping the database ports closed to the public internet.


