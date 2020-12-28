# my-Nextcloud
lorem ipsum, lorem ipsum
lorem ipsum

# Description
lorem ipsum, lorem ipsum
lorem ipsum

# Table of Contents
lorem ipsum, lorem ipsum
lorem ipsum

# Installation
lorem ipsum, lorem ipsum
lorem ipsum

### Enable cache
go to

```php

<?php
$CONFIG = array (
  'memcache.local' => '\\OC\\Memcache\\APCu',
  'memcache.distributed' => '\\OC\\Memcache\\Redis',
  'memcache.locking' => '\\OC\\Memcache\\Redis',
  'redis' => [
    'host' => 'xxx.xxx.xxx.xxx', # set your host IP address here
    'port' => 6379,
  ],
  'datadirectory' => '/data',
  'instanceid' =>  # will be created automatically during container initialization 
  'passwordsalt' =>  # will be created automatically during container initialization
  'secret' =>  # will be created automatically during container initialization
  'trusted_domains' => 
  array (
    0 => 'xxx.xxx.xxx.xxx', # set your host IP address here
  ),
  'dbtype' => 'mysql',
  'version' => '20.0.3.2',
  'overwrite.cli.url' => 'https://xxx.xxx.xxx.xxx', # set your host IP address here
  'dbname' => 'ncdb',
  'dbhost' => 'db',
  'dbport' => '',
  'dbtableprefix' => 'oc_',
  'dbuser' => 'nextcloud',
  'dbpassword' => 'xxxx',
  'installed' => true,
);

```

# Usage
lorem ipsum, lorem ipsum
lorem ipsum
