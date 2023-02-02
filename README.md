# apache-superset

Superset is open-source, fast, lightweight, intuitive, and loaded with options that make it easy for users of all skill sets to explore and visualize their data, from simple line charts to highly detailed geospatial charts.

[![official website](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Superset_logo.svg/768px-Superset_logo.svg.png?20210129193338)](https://superset.apache.org/)

## Installation

Follow these steps to install superset==1.5.3 on ubuntu or AWS EC2 instance:

* Install dependencies:

  ```
  sudo apt-get install build-essential libssl-dev libffi-dev python3-dev python3-pip libsasl2-dev libldap2-dev default-libmysqlclient-dev
  ```

* Different python versions can be obtained from deadsnake’s ppa:

  ```
  sudo add-apt-repository ppa:deadsnakes/ppa
  ```

* Check for any updates:

  ```
  sudo apt update
  ```

* Now, we have to install a few python stuff, superset requires python version 3.8, so we have downgrade the version:

  ```
  sudo apt install python3.8 python3.8-dev python3.8-venv
  sudo apt install build-essential
  ```

* Now we can start installation:

  ```
  python3.8 -m venv venv
  source venv/bin/activate
  pip install apache-superset==1.5.3
  ```
  
* Important to remember, we have to install dependencies which is comaptible with superset, here we are installing snowflake connector for example, change this to your required database:

  ```
  pip install snowflake-connector-python==2.7.9
  pip install snowflake-sqlalchemy==1.2.4
  pip install typing-extensions==3.10.0.0
  pip install SQLAlchemy==1.3.16
  pip install SQLAlchemy-Utils==0.37.9 
  ```

* The markupsafe version is broken. We have to downgrade it.:

  ```
  pip install markupsafe==2.0.1
  
  ```
* The pyopenssl version is broken. We have to downgrade it.:

  ```
  pip uninstall pyopenssl
  pip install pyopenssl==22.1.0
  ```
  
* Now proceed with superset initializations:

  ```
  export FLASK_APP=superset
  superset fab create-admin
  superset db upgrade
  superset load_examples
  superset init
  ```

* Finally you can run it. Remember to open port 8088:

  ```
  superset run -p 8088 -h 0.0.0.0 --with-threads --reload --debugger
  
  ```

## License

Copyright (C) 2023 Rajath C R <rajathcr14@gmail.com>

