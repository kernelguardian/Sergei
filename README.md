# Sergei

Sergei is a django app for JWT operations, completely customizable and flexible.

Sergei lifts all the heavyweight for you, yes we also threw in redis into it, because why not ¯\_(ツ)_/¯


## Getting Started
1. Please start with a virtualenvironment 
    ```bash
    $ virtualenv ENV
    $ ENV\Scripts\activate
    (ENV)$ 
    ```
2. Install the packages
    ```bash
    $ pip install -r requirements.txt
    ```
3. Configure your Sergei settings
    You can either use Redis or SQL default db(haven't tested against postgresql) for blacklisting tokens // I am not judging you :) or without either of them ( no blacklisting it is then)

    1. With SQL database

       1. Enable SQL based blacklisting off by updating the below fields (IMPORTANT)
          ```json
          ...
            "POSTGRESQL": {
                "OutstandingToken": True,
                "BlacklistToken": True
                ...
          ```
        2. Run migrations to generate the tables
            ```bash
            python manage.py makemigration
            python manage.py migrate
            ```
    2. Without SQL database or Redis // No token blacklisting
        Update the follwing values

        ```json
            ...
            "REDIS": {
                "REQUIRED": False,
                ...
        ```
        
        ```json
            "POSTGRESQL": {
            "OutstandingToken": False,
            "BlacklistToken": False
        ```
    3. With Redis

        1. Change `REQUIRED` to True in the `settings.py` file
           ```json
            ...
            "REDIS": {
                "REQUIRED": True,
                ...
           ```
        2. Update the Redis configuration in `.env` file (check .env.example for sample configuration)
        3. Disable SQL based blacklisting off by updating the below fields (IMPORTANT)
           ```json
            ...
            "POSTGRESQL": {
                "OutstandingToken": False,
                "BlacklistToken": False
                ...
           ```





## How to use this package?
1. You can either use the provided views as is or extend them to your need
2. Or you can import the JWT Core functionalities from `authentication_app\JWT\core.py` file in your views. Check documentation for more.


Use <a href="https://www.getpostman.com/collections/34eca3f12a93d192c160">Postman collection</a> 


DOCUMENTATION WILL BE ADDED SOON

DISCLAIMER: NOT INTENDED TO BE USED IN PRODUCTION


# Lots of breaking changes incoming + expect a installable package soon because why not ¯\_(ツ)_/¯
