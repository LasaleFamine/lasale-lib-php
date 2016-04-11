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
    	"active": true					// Determine if related methods are active after initialization
        "host": "hostOfYourDB",
        "port": "portOfYourSQLDb", 
        "name": "DBname",
        "username": "DBusername",
        "password": "userPasswordForDB"
    },

    "rssParser": {
    	"active": true
    }
}
```
#### Create a config PHP file
If you don't have one, you may want to create a new `config.php` file and including it in every single PHP file of your application
Ex:
```php
<?php

require("/path/to/LaSale.php");
LaSale::init(__DIR__ . "/path/to/config.json");

?>
```
#### Usage
Simple usage
```php
<?php

// Require configuration
require("../includes/config.php");
// Use a method
$result = LaSale::method();

?>
```
## Methods
### `query` 
Use to get results from your SQL DB pre-configured. You can pass variables to the methods that will check the validity of the value.
Ex:
```php
<?php

$row = LaSale::query('SELECT * from table1 where param = ?', $varParam);

?>
```
##### Returns
Error:  
`string` --> Specific error  

SELECT query:  
`array` -->  All rows selected  

DELETE, INSERT, or UPDATE query:  
`int` -->  Number of rows affected

### `parseRss` 
Parse any Atom/RSS using this method. It loads an helpful library written by Arian Stolwijk (https://github.com/arian/Rss-Parser) with a little fork by me.
Ex:
```php
<?php

$LaSale = new LaSale();
$rss = $LaSale->parseRss("http://www.linktorss.com/feed/");
$rss2 = $LaSale->parseRss("http://www.linktoanotherrss.com/feed/");

?>
```
##### Returns  
`obj` --> RSS object

#### Helper Submethods
##### - `getItems` --> Get every items
##### - `getLink` --> Get link from an item
##### - `getTitle` --> Get tile from
##### - `getPubDate` --> Get publish date
Ex:
```php
<?php
$LaSale = new LaSale();
$rss = $LaSale->parseRss('http://www.linktorss.com/feed/');

foreach($rss->getItems() as $item){
	echo '<a href="'.$item->getLink().'">'.$item->getTitle().'</a><br /> <span>'.$item->getPubDate().'</span>';
}

?>
```


