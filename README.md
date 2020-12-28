# my-Nextcloud
[Nextcloud](https://nextcloud.com/) is an open source, self-hosted file sync, sharing and communication app platform. The *my-nextcloud* project is all about setting up a Nextcloud instance on a server in your home network for document sharing and collaboration within your family. 

# Description
This is about installing Nextcloud, MariaDB and Redis using [Docker](https://www.docker.com/) and [Docker-Compose](https://docs.docker.com/compose/) on a Raspberry Pi. The installation runs behind your router in your home network only. You can make Nextcloud accessable from the internet. However, that's not part of this guide.  

# Table of Contents
lorem ipsum, lorem ipsum
lorem ipsum

# Installation
lorem ipsum, lorem ipsum
lorem ipsum

These are the main steps to be executed:
1. setup your Raspberry Pi
1. install external USB drive as mass storage device (optional but recommended) 
1. install docker and docker-compose on your Raspberry Pi
1. setup your docker project structure
1. create your docker-compose.yml file
1. start up your applications
1. enjoy Netxcloud :smiley:

### Software Installation
Get the [Raspberry Pi OS](https://www.raspberrypi.org/software/) of your choice and flash to your SD card. There are guides available on the internet for all popular operating systems on how to flash an image to a SD card. If you're planning to run your Raspi headless you my want to use the **Lite** version. Keep in mind to enable **ssh** access by placing a file named ` ssh `, without any extension, onto the boot partition of the SD card from another computer. When the Pi boots, it looks for the ssh file. If it is found, SSH is enabled and the file is deleted. The content of the file does not matter; it could contain text, or nothing at all.

Next install Docker and Docker-Compose on your Pi. If you're looking for help, start here: [Docker comes to Raspberry Pi](https://www.raspberrypi.org/blog/docker-comes-to-raspberry-pi/).

### Project Structure

### Enable caching
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
