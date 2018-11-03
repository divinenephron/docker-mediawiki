# Docker Compose file showing how to install plugins in the official MediaWiki image

## Installation

### Install Docker

Install Docker according to the [official
instruction](https://docs.docker.com/install/linux/docker-ce/debian/#install-using-the-repository).

### Configure database usernames and password

The database usernames and passwords aren't stored in this repository,
so you'll have to create the file which contain them yourself. First
create the file `mysql_secrets` with the following, replacing the text
in square brackets with what ever you want:

```
MYSQL_DATABASE=[mysql_database]
MYSQL_USER=[mysql_username]
MYSQL_PASSWORD="[mysql_password]"
```

Then create the file `mediawiki_secrets` with the following, replacing
the text in square brackets so it matches the contents of
`mysql_secrets`.

```
<?php
$wgDBname = "[mysql_database]";
$wgDBuser = "[mysql_username]";
$wgDBpassword = "[mysql_password]";
```

### Create a MediaWiki image with the plugins you need

The file `mediawiki/Dockerfile` adds the plugins I use to the [official
MediaWiki docker image](https://hub.docker.com/_/mediawiki/). Turn
this into a usable image using the following:

```
$ docker build -t divinenephron/mediawiki mediawiki
```

### Start MediaWiki and the services it needs

`docker-compose.yml` contain instructions for launching the
`divinenephron/mediawiki` image created above along with the other
containers it needs to work. Together these containers are called a
"stack".

Start the stack using:

```
$ docker swarm init
$ docker stack deploy -c docker-compose.yml my-mediawiki
```

Stop the stack using:

```
$ docker stack rm my-mediawiki
$ docker swarm leave --force
```
