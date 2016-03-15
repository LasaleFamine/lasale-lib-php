# lasale-lib-php
Utility library for PHP

## Installation
First donwload the file or clone the repo
```sh
$ git clone https://github.com/LasaleFamine/lasale-lib-php [optional name]
```
Copy the file `LaSale.php` inside your choosen directory. 

## Configuration
#### Create a config JSON file
You need a `config.json` file to initialize the library correctly.  
Ex: 
```js
{
    "database": {
        "host": "hostOfYourDB",
        "port": "portOfYourSQLDb", 
        "name": "DBname",
        "username": "DBusername",
        "password": "userPasswordForDB"
    }
}
```
#### Create a config PHP file
If you don't have one
