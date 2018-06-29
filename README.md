# Linux Server Configuration

This project takes a baseline installation of Ubuntu Linux on [AWS Lightsail](https://aws.amazon.com/lightsail/) and prepares it to host a web application.  The [Exercise Catalog project](https://github.com/courtg47/exercise-catalog) is served and all security and firewall settings are configured. This project satisfies the Linux Server Configuration project from Udacity's Full Stack Web Developer curriculum.


## Accessing the Server

To access this server, you will need to remotely login via your linux terminal/command line using the following information:

* IP Address: 13.58.51.172
* URL: http://13.58.51.172.xip.io
* SSH Port: 2200
* Username: `grader`

SSH key required to access this project for purposes of grading will be sent in the *Notes to the Reviewer* field on submission.


## Software Installed

* Apache2
* mod_wsgi
* Python
* Flask
* PostgreSQL
* SQLAlchemy
* virtualenv
* psycopg2
* httplib2
* request
* oauth2client


## Configurations to the Server

* Updated and upgraded installed packages
* Installed finger
* Configured Uncomplicated Firewall (UFW) to allow all outgoing
  and only allow incoming on ports 2200 (SSH), 80 (HTTP), and 123 (NTP).
* Changed default SSH port from 22 to 2200 on the AWS Lightsail console (Networking > Firewall)
* Changed default SSH port from port 22 to port 2200 in UFW.
* Created user account named `grader` and gave `sudo` access
* Created `SSH` login for `grader`
* Configured local time to UTC
* Enforced key-based authentication in the `/etc/ssh/sshd_config` file
* Disabled password logins
* Disabled SSH login for root user
* Installed apache and mod_wsgi
* Started Apache service
* Installed and configured git
* Created `catalog` directory in the `/var/www/` file path
* Cloned the [Exercise Catalog app from Github](https://github.com/courtg47/exercise-catalog) into the `catalog` directory
* Made the following changes to the code:
  * Renamed `application.py` to `__init__.py`
  * Included absolute file path for `client_secrets.json` file in `__init__.py`
  * Changed DB connection string in `database_setup.py` and `__init__.py` to access DB via the `catalog` user's credentials.
  * Changed `app.run(host='0.0.0.0', port=8000)` in the main function to `app.run()` in __init__.py
* Installed virtual environment in the same directory as the app project via `virtualenv` command. Named it `VM`.
* Inside the virtual environment, installed all dependencies listed under *Software Installed* section
* Created virtual host config file in the `/etc/apache2/sites-available` directory called `catalog.conf`
* Created and configured the `catalog.wsgi` file in the `/var/www/catalog` directory
* Installed PostgreSQL and created new database `catalog` as `postgres` user
* Cloned database dump from Github into empty directory in the `catalog` directory
* Populated empty `catalog` database with DB dump
* Created postgreSQL user `catalog` with password
* Gave user `catalog` full permissions for `catalog` DB
* Secured database by revoking public rights and disabling remote connections
* Ran `database_setup.py`
* Altered JavaScript Origins and redirect URIs in the Google Signin API key
* Copied new client secrets into `client_secrets.json` file
* Changed settings in the `/etc/apache2/conf-enabled/security.conf` file to ensure the `.git` directory was not publicly accessible via   the browser.
* In the virtual machine, restarted apache service and ran `__init__.py`
* Accessed the served application at the above stated URL.


## Third-Party Resources

* [Xip.io](http://xip.io/) - a wildcard DNS service used to test web applications without registering a domain name. This was utilized for JavaScript origins in the Google Sign In API key. Requires adding `xip.io` to the end of an IP address.

* [Amazon Lightsail](https://aws.amazon.com/lightsail/) - A cloud-based virtual private server with Amazon Web Services (AWS).

