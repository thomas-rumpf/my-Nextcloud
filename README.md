# my-Nextcloud
[Nextcloud](https://nextcloud.com/) is an open source, self-hosted file sync, sharing and communication app platform. The **my-Nextcloud** project is all about setting up a Nextcloud instance on a server in your home network for document sharing and collaboration within your family. 

# Description
This is about installing Nextcloud, MariaDB and Redis using [Docker](https://www.docker.com/) and [Docker-Compose](https://docs.docker.com/compose/) on a Raspberry Pi. The installation runs behind your router in your home network only. You can make Nextcloud accessable from the internet. However, that's not part of this guide.  

For this installation I am using the following images
- [x] linuxserver/nextcloud
- [x] linuxserver/mariadb
- [x] redis

Please note that by the time of writing this guide the latest MariaDB version had an issue that prevented nextcloud from connecting to the database. Refer to https://github.com/nextcloud/docker/issues/1038 for details. That's why I used a 10.3.x version of MariaDB in docker-compose. 

# Installation
These are the main steps to be executed:
1. setup your Raspberry Pi
1. install docker and docker-compose on your Raspberry Pi
1. install external USB drive as mass storage device (optional but recommended) 
1. setup your docker persistent volumes
1. create your docker-compose.yml file
1. start up your applications
1. tweak your configuration for performance
1. enjoy Netxcloud :smiley:

### Software Installation
Get the [Raspberry Pi OS](https://www.raspberrypi.org/software/) of your choice and flash to your SD card. There are guides available on the internet for all popular operating systems on how to flash an image to a SD card. If you're planning to run your Raspi headless you may want to use the **Lite** version. Keep in mind to enable **ssh** access by placing a file named ` ssh `, without any extension, onto the boot partition of the SD card from another computer. When the Pi boots, it looks for the ssh file. If it is found, SSH is enabled and the file is deleted. The content of the file does not matter; it could contain text, or nothing at all.

Next install Docker and Docker-Compose on your Pi. If you're looking for help, start here: [Docker comes to Raspberry Pi](https://www.raspberrypi.org/blog/docker-comes-to-raspberry-pi/).

### Persistent Volumes
If you intend to run your nextcloud for more than just some testing, you would want to make your data stay safe even though your container may vanish or in case your app needs upgrading. The preferred mechanism for that are docker volumes that provide a means to make your data persistent. For this installation to work you will need to create certain volumes on your Raspberry Pi and mount them during the container start up. In case you want to use different images (e.g. the standard nextcloud image instead of the Linuxserver.io image) go check the image description for which volumes can be mapped. 

For this installation to work I've put the following directory structure in place on the Raspberry Pi:

```
my-nextcloud/
  app/
    config # this is where my nextcloud configuration data lives
  cache
  db/
    config # this is where my mariadb data lives
```

Additionally I've created a mount point ` /mnt/usb ` for an external USB drive to host nextcloud user data. You will need to reference these folders in your docker-compose.yml file; refer to ` my-Nextcloud/docker-compose.yml `.

### Enable caching
After you have started your containers with ` docker-compose up -d ` you will need to tweak your nextcloud configuration a bit in order to benefit from redis caching. Go to ` path/to/nextcloud/config/ ` and open ` config.php `. Add the following lines to enable the redis cache:

```php

  'memcache.distributed' => '\\OC\\Memcache\\Redis',
  'memcache.locking' => '\\OC\\Memcache\\Redis',
  'redis' => [
    'host' => 'xxx.xxx.xxx.xxx', # set your host IP address here
    'port' => 6379,
  ],

```

In case you want to verify redis cache is enabled open a terminal and ssh into your Pi. Go to the directory that contains your docker-compose.yml file. 
You will need to get into the redis container with the following command ` docker exec -it redis sh `. Now enter ` redis-cli ` and ` monitor `. You'll get an OK message. Leave the terminal open while you access your Nextcloud via the browser. If you see log messages being displayed on the terminal while brwosing your nextcloud files and photos, redis cache is working.

# Usage
Go to the directory that contains your docker-compose.yml file. 
Start your containers with ` docker-compose up -d `.
Now you should be able to access your nextcloud instance using your browser.
Simply put the IP address of your Pi into the browser and off you go :smiley:
