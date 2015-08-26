How to create a new user and grant permissions in MySQL
No Comments	Tagged In centos, debian, MySQL, permissions, ubuntu, users

MySQL is one of the most popular database management systems. In this tutorial we will cover the steps needed to create new MySQL user and grant permissions to it in CentOS 6.4, Debian or Ubuntu platform.
Requirements

        CentOS 6.4, Debian or Ubuntu installed on your computer/server
        SSH access (Command line access to the server)
        root privileges
        Basic skills for working on a Linux environment
        LAMP installed on the server

All operation will be executed inside a MySQL prompt with the root user:
1
	
mysql -p -u root

You will be prompted to fill in the MySQL root password.
Create a new user

We can create new MySQL user with the following command:
1
	
CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';

where:

            user – the name of the MySQL user which will be created
            password – the password which we want to assign to that user

All MySQL commands are engin with a semicolon (;).
Grant permissions for a user

The next thing that we will have to do is to grant privileges for that user in order to be able to access the MySQL client and to work with the corresponding database/s:
1
	
GRANT ALL PRIVILEGES ON database.table TO 'user'@'localhost';

where:

            database – the name of the MySQL database to which we grant access
            table – the name of the database table to which we grant access

We are allowed to use the asterisk wildcard symbol (*) when we want to grant access to all databases/tables:
1
	
GRANT ALL PRIVILEGES ON database.* TO 'user'@'localhost';

or
1
	
GRANT ALL PRIVILEGES ON *.* TO 'user'@'localhost';

With the first command we grant all privileges to the MySQL user to all database tables related to the database with name "database".
In the second case access for the user is granted to all databases.

Here is a list of the MySQL privileges which are most commonly used:

            ALL PRIVILEGES – grants all privileges to the MySQL user
            CREATE – allows the user to create databases and tables
            DROP - allows the user to drop databases and tables
            DELETE - allows the user to delete rows from specific MySQL table
            INSERT - allows the user to insert rows into specific MySQL table
            SELECT – allows the user to read the database
            UPDATE - allows the user to update table rows

Here is a sample syntax where only two privileges are granted for the user:
1
	
GRANT SELECT, INSERT, DELETE ON database.* TO 'user'@'localhost';

In order for the changes to take effect and the privileges to be saved the following command should be executed at the end:
1
	
FLUSH PRIVILEGES;

Remove an existing MySQL user

A MySQL user can be deleted with the following command:
1
	
DROP USER 'user'@'localhost'
