Crontab UI — Glassmorphic Fork
==============================

> **This is a fork of [alseambusher/crontab-ui](https://github.com/alseambusher/crontab-ui) with a glassmorphic UI reskin.**
> The original npm package installs the plain Bootstrap UI. Install from this repo to get the glassmorphic theme.

[![npm](https://img.shields.io/npm/l/crontab-ui.svg?style=flat-square)](https://lifepluslinux.blogspot.com/2015/06/crontab-ui-easy-and-safe-way-to-manage.html)

Editing the plain text crontab is error prone for managing jobs, e.g., adding jobs, deleting jobs, or pausing jobs. A small mistake can easily bring down all the jobs and might cost you a lot of time. With Crontab UI, it is very easy to manage crontab. Here are the key features of Crontab UI.

1. Easy setup. You can even import from existing crontab.
2. Safe adding, deleting or pausing jobs. Easy to maintain hundreds of jobs.
3. Backup your crontabs.
4. Export crontab and deploy on other machines without much hassle.
5. Error log support.
6. Mailing and hooks support.

## What's different in this fork

- **Glassmorphic UI** — Aurora gradient background (teal-green-blue), frosted glass panels, navbar, modals, and table
- All Bootstrap JS functionality (modals, dropdowns, DataTables) is fully preserved

## Setup

### Install from this fork (gets the glassmorphic UI)

```bash
git clone https://github.com/lubabs770/crontab-ui-gamify.git
cd crontab-ui-gamify
npm install
npm start
```

### Install the original (plain Bootstrap UI)

Get latest `node` from [here](https://nodejs.org/en/download/current/). Then,

    npm install -g crontab-ui
    crontab-ui

If you need to set/use an alternative host, port OR base url, you may do so by setting an environment variable before starting the process:

    HOST=0.0.0.0 PORT=9000 BASE_URL=/alse crontab-ui

By default, db, backups and logs are stored in the installation directory. It is **recommended** that it be overriden using env variable `CRON_DB_PATH`. This is particularly helpful in case you **update** crontab-ui.

    CRON_DB_PATH=/path/to/folder crontab-ui
    
If you need to apply basic HTTP authentication, you can set user name and password through environment variables:

    BASIC_AUTH_USER=user BASIC_AUTH_PWD=SecretPassword
    
Also, you may have to **set permissions** for your `node_modules` folder. Refer [this](https://docs.npmjs.com/getting-started/fixing-npm-permissions).

If you need to use SSL, you can pass the private key and certificate through environment variables:

    SSL_CERT=/path/to/ssl_certificate SSL_KEY=/path/to/ssl_private_key

Make sure node has the correct **permissions** to read the certificate and the key.

If you need to autosave your changes to crontab directly:

    crontab-ui --autosave

### List of ennvironment variables supported
- HOST
- PORT
- BASE_URL
- CRON_DB_PATH
- CRON_PATH
- BASIC_AUTH_USER, BASIC_AUTH_PWD
- SSL_CERT, SSL_KEY 
- ENABLE_AUTOSAVE


## Docker
You can use crontab-ui with docker. You can use the prebuilt images in the [dockerhub](https://hub.docker.com/r/alseambusher/crontab-ui/tags)
```bash
docker run -d -p 8000:8000 alseambusher/crontab-ui
```

You can also build from this fork to get the glassmorphic UI:
```bash
git clone https://github.com/lubabs770/crontab-ui-gamify.git
cd crontab-ui-gamify
docker build -t crontab-ui-gamify .
docker run -d -p 8000:8000 crontab-ui-gamify
```

If you want to use it with authentication, You can pass `BASIC_AUTH_USER` and `BASIC_AUTH_PWD` as env variables
```bash
docker run -e BASIC_AUTH_USER=user -e BASIC_AUTH_PWD=SecretPassword -d -p 8000:8000 alseambusher/crontab-ui 
```

You can also mount a folder to store the db and logs.
```bash
mkdir -p crontabs/logs
docker run --mount type=bind,source="$(pwd)"/crontabs/,target=/crontab-ui/crontabs/ -d -p 8000:8000 alseambusher/crontab-ui
```

If you are looking to modify the host's crontab, you would have to mount the crontab folder of your host to that of the container. 
```bash
# On Ubuntu, it can look something like this and /etc/cron.d/root is used
docker run -d -p 8000:8000 -v /etc/cron.d:/etc/crontabs alseambusher/crontab-ui
```

    
## Resources

* [Full usage details](https://lifepluslinux.blogspot.com/2015/06/crontab-ui-easy-and-safe-way-to-manage.html)
* [Issues](https://github.com/alseambusher/crontab-ui/blob/master/README/issues.md)
* [Setup Mailing after execution](https://lifepluslinux.blogspot.com/2017/03/introducing-mailing-in-crontab-ui.html)
* [Integration with nginx and authentication](https://github.com/alseambusher/crontab-ui/blob/master/README/nginx.md)
* [Setup on Raspberry pi](https://lifepluslinux.blogspot.com/2017/03/setting-up-crontab-ui-on-raspberry-pi.html)

### Adding, deleting, pausing and resuming jobs.

Once setup Crontab UI provides you with a web interface using which you can manage all the jobs without much hassle.

![basic](https://github.com/alseambusher/crontab-ui/raw/gh-pages/screenshots/main.png)

### Import from existing crontab

Import from existing crontab file automatically.
![import](https://github.com/alseambusher/crontab-ui/raw/gh-pages/screenshots/import.gif)

### Backup and restore crontab

Keep backups of your crontab in case you mess up.
![backup](https://github.com/alseambusher/crontab-ui/raw/gh-pages/screenshots/backup.png)

### Export and import crontab on multiple instances of Crontab UI.

If you want to run the same jobs on multiple machines simply export from one instance and import the same on the other. No SSH, No copy paste!

![export](https://github.com/alseambusher/crontab-ui/raw/gh-pages/screenshots/import_db.png)

But make sure to take a backup before importing.

### Separate error log support for every job
![logs](https://github.com/alseambusher/crontab-ui/raw/gh-pages/screenshots/log.gif)

### Donate
Like the project? [Buy me a coffee](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=U8328Q7VFZMTS)!

### Original project
This fork is based on [alseambusher/crontab-ui](https://github.com/alseambusher/crontab-ui). For issues unrelated to the glassmorphic UI, refer to the upstream repo.

### License
[MIT](LICENSE.md)
