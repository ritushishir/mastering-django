#### Local MySQL Server Setup

##### ⚙️ Install MySQL Server

- For macOS using Homebrew:
  ```bash
  brew install mysql
  ```
- For Ubuntu/Debian:
  ```bash
  sudo apt-get install mysql-server
  ```
- For Windows, download the installer from the [MySQL website](https://dev.mysql.com/downloads/installer/).

##### 🔐 Secure MySQL Installation

```bash
sudo mysql_secure_installation
```

Follow the prompts to set a root password and secure your installation.

###### Confirm the MySQL Service is Running

Login to the MySQL shell:

```bash
mysql -uroot -p
```

You should see something like the following:
![alt text](assets/mysql-shell.png)

And then check the existing databases:

```bash
show databases;

```

##### ➕ Create the Database and User

Using your root user/password, you can create a new database and user with the following commands:

```sql
CREATE DATABASE geetshala;
CREATE USER 'djangouser'@'localhost' IDENTIFIED BY 'djangopassword';
GRANT ALL PRIVILEGES ON geetshala.* TO 'djangouser'@'localhost';
```

##### Expected Output

- MySQL server should be up and running.
- You should be able to log in to the MySQL shell using the root user.
- Database `geetshala` created. Verify by running `show databases;`.
- User `djangouser` created with password `djangopassword` and granted privileges on the `geetshala` database.
