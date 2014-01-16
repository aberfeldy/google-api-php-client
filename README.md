# Google APIs Client Library for PHP #

## Description ##
The Google API Client Library enables you to work with Google APIs such as Google+, Drive, or YouTube on your server.
Changed from "require_once" to using namespaces for integration into frameworks (like Laravel)

## Requirements ##
* [PHP 5.2.1 or higher](http://www.php.net/)
* [PHP JSON extension](http://php.net/manual/en/book.json.php)

## Installation ##

Open composer.json and add following line section
```json
"repositories": [
        {
            "aberfeldy/apiclient": "*"
        }
    ],
"require": {
       "aberfeldy/apiclient": {
           "type": "vcs",
           "url": "git@github.com:aberfeldy/google-api-php-client.git"
       }
}
```

## Developer Documentation ##
http://developers.google.com/api-client-library/php

## Basic Example ##
See the examples/ directory for examples of the key client features.
```PHP
<?php
  $client = new GoogleApi\Google_Client();
  $client->setApplicationName("Client_Library_Examples");
  $client->setDeveloperKey("YOUR_APP_KEY");
  $service = new GoogleApi\Service\Google_Service_Books($client);
  $optParams = array('filter' => 'free-ebooks');
  $results = $service->volumes->listVolumes('Henry David Thoreau', $optParams);

  foreach ($results as $item) {
    echo $item['volumeInfo']['title'], "<br /> \n";
  }
```

## Code Quality ##

Copy the ruleset.xml in style/ into a new directory named GAPI/ in your
/usr/share/php/PHP/CodeSniffer/Standards (or appropriate equivalent directory),
and run code sniffs with:

        phpcs --standard=GAPI src/

