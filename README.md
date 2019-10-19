# Components
* Base Image: Ubuntu 16.04
* Apache2
* PHP 5.6
* Apache Subversion
* iF.SVNAdmin (Credits: http://svnadmin.insanefactory.com/. It's a web interface for subversion repositories and users management . http://svnadmin.insanefactory.com/screenshots/)

## Usage
```sh
git clone https://github.com/ZevenFang/docker-svn-ifsvnadmin svnadmin
docker run --name svnadmin -it -dp 8008:80 \
-v "${PWD}/svnadmin/data":/var/www/html/svnadmin/data \
-v "${PWD}/svnadmin/repo":/home/ubuntu/svndata \
-v "${PWD}/svnadmin/conf":/etc/apache2/conf \
zevenfang/svnadmin
```
Then visit `http://localhost:8008/svnadmin`

## Setting
Subversion authorization
`/etc/apache2/conf/access_svn`
User authentication
`/etc/apache2/conf/dav_svn.passwd`
SVNParentPath
`/home/ubuntu/svndata`
Subversion client executable
`/usr/bin/svn`
Subversion admin executable
`/usr/bin/svnadmin`

## Volumes

| Container Folder               | Description                                                                   |
| ------------------------------ | ----------------------------------------------------------------------------- |
| `/var/www/html/svnadmin/data/` | Data folder of IF.SVNAdmin for config.ini and userroleassignments.ini         |
| `/home/ubuntu/svndata/`        | Repositories folder                                                           |
| `/etc/apache2/conf/`           | Apache subversion folder for access_svn and dav_svn.passwd files              |

## Ports
**`80 TCP/IP`**

## URL Endpoints

| App URL                                   | Description                     |
| ----------------------------------------- | ------------------------------- |
| `http://serverip/svnadmin`                | Endpoint for iF.SVNAdmin        |
| `http://serverip/svnrepos/myRepo`         | Endpoint for SVN myRepo example |

## Environment variables

| Env Var            | Default value               |
| ------------------ | --------------------------- |
| `SVN_LOCATION`     | svnrepos                    |
