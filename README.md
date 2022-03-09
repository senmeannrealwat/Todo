# Todo Server Setup

### Requirements
##### Server
  - Ubuntu >16.04.4 LT
  - Language - Python 3.8.0
  - Framework - Django 2.2.0
  - Database Server - PostgreSQL 9.5.12
### Installation
[Git](https://help.ubuntu.com/lts/serverguide/git.html) and [Virtualenvwrapper](http://virtualenvwrapper.readthedocs.io/en/latest/install.html) need in this installation
  - Install pip
    ```sh
      $ wget https://bootstrap.pypa.io/get-pip.py
      $ python get-pip.py
    ```
    If there is an error ```PermissionError: [Errno 13] Permission denied: '/usr/local/lib/python3.5/dist-packages/pip'```. Use command with root peremission ```$ sudo python get-pip.py```

  - Install Git
    ```sh
    $ sudo apt update
    $ sudo apt install git
    ```

  - Install Postgres
    ```sh
    $ sudo apt install postgresql postgresql-contrib libpq-dev
    ### set password for postgres ###
    $ sudo -u postgres psql postgres
    \password postgres
    ### enter password when it prompt ###
    \q
    $ sudo -u postgres createdb [database name]
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

### Configuring and Running

  - Clone the source code from github

    assume that we will place the source code to /opt/project, if the directory doesn't exists please create one by
    ```sh
      $ sudo mkdir /opt/project
      $ sudo chown username:www-data /opt/project
      $ sudo chmod 775 /opt/project
      $ cd /opt/projectorigin https://github.com/senmeannrealwat/Todo.git
    ```

  - Create virtualenv and install python package from ```TradeDesk_Backend/requirements.txt```
    ```sh
      $ mkvirtualenv todo-env
      (todo-env)$ pip install -r /opt/project/Todo/requirements.txt
      $ cd /opt/project/Todo
      $ python manage.py migrate
      $ python manage.py cities_light
      # Run this command and follow the instruction to create superuser for site admin
      $ python manage.py createsuperuser
     ```
    - Configuring sending email
      ```sh
        $ Open setting.py file at directory $ cd  /opt/project/Todo/Todo
          Add you real Emial and Password To 
           EMAIL_HOST_USER = '--------'
           EMAIL_HOST_PASSWORD = '*******'
        
      
   - Api 
     1. Register: http://127.0.0.1:8000/api/user/register
     2. Login: http://127.0.0.1:8000/api/user/login
     3. Reset Password: http://127.0.0.1:8000/password-reset
