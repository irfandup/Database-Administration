## Installing Postgresql 16 on Rocky Linux 8.10

Step 1: List available versions

```Bash
dnf module list postgresql
```
Step 2: Enable your preferred version (e.g., 16)

```Bash
sudo dnf module enable postgresql:16 -y
```
Step 3: Install the server

```Bash
sudo dnf install postgresql-server -y
```
Step 4: Initialize the database
Unlike MySQL, PostgreSQL requires a manual initialization of its storage directory.

```Bash
sudo postgresql-setup --initdb
```
Step 5: Start and Enable the service

```Bash
sudo systemctl enable --now postgresql
```
Step 6: Access the PostgreSQL shell
Switch to the default postgres system user to log in.

```Bash
su - postgres
psql
```
