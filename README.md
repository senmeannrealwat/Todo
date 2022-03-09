# Todo Setup Server

### Requirements
##### Server
  - Ubuntus 20>
  - Language - Python 3.8.0
  - Framework - Django 2.2.0
  - Database Server - PostgreSQL 9.5.12
  - Other ([wkhtmltopdf](https://wkhtmltopdf.org/downloads.html))
- Install Postgres
    ```sh
    $ sudo apt install postgresql postgresql-contrib libpq-dev
    ### set password for postgres ###
    $ sudo -u postgres psql postgres
    \password postgres
    ### enter password when it prompt ###
    \q
    $ sudo -u postgres createdb [TradeDesk database name]
    ```
    TradeDesk database ```name```, database ```user```, ```port``` and ```password``` will be need for setting ```Evironment Varianbles```

  - Install [VirtualenvWrapper](http://virtualenvwrapper.readthedocs.io/en/latest/install.html)
    ```sh
    $ sudo pip install virtualenvwrapper
    ```
    if you see any error related to "Six" module please use this command ```$ sudo pip install virtualenvwrapper --ignore-installed six``` to install virtualenvwrapper

    1. Create a directory to hold the virtual environments.
    ```sh
      $ sudo mkdir /opt/.virtualenvs
      # Please replace username to the current logged in user
      $ sudo chown username:www-data /opt/.virtualenvs/
      $ sudo chmod 775 /opt/.virtualenvs/
    ```
    2. Add a line like ```export WORKON_HOME=/opt/.virtualenvs``` to your .bashrc.
    3. Add a line like ```source /usr/local/bin/virtualenvwrapper.sh``` to your .bashrc.
    4. Run: ``` $ source ~/.bashrc```
