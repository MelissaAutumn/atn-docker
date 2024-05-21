# Addons Server Docker
An approximate docker image of Thunderbird's addons server that works on my macbook. 

It's split out into a separate repo so I can use it without affecting the docker image residing in addons-server.

## Setup

Clone [Thunderbird's addons server](https://github.com/thunderbird/addons-server) to `./addons-server` and run `docker-compose --build`. 

You may have to do [some tweaks](https://github.com/thunderbird/addons-server/pull/226/files) to get addons generated for Thunderbird. Once you do, and have a working database you can revert those tweaks.

You might also want to add `disable-lwt-uploads` as a waffle_switch entry in the database to get rid of some missing routes error.

## Local Authentication

Apply the patch `patches/login_override.patch` and then navigate to: `http://olympia.test:8000/api/v3/accounts/login/start/` to authenticate locally. Please don't commit this change!

## Python 3

See https://github.com/mozilla/addons/issues/6305 for web3 container instructions
https://github.com/mozilla/addons-server/pull/10337/