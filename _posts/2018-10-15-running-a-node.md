---
layout: post
title: "Running a Monero node"
category: blog
summary: "Running a node is easy - but only if you know how"
author: m2049r
tags: [node]
---

## Monero Nodes

Nodes store a copy of the Monero blockchain and share it with each 
other. No nodes = no Monero. And we don't want that.

A Monero wallet app (like Monerujo, but also the official GUI & CLI) 
needs to connect to a node to talk with the Monero network. So running 
your own node also increases your level of privacy and security since 
no one else will know you are using your wallet.

This guide will show you how to run one on Ubuntu 18.04.

## But I don't have Ubuntu!

Just get one from a VPS provider like 
[scaleway](https://www.scaleway.com/)
or [hetzner](https://www.hetzner.com/) - let a friend help you! The 
only real constraint is the space needed for the blockchain. 
At the time of writing the blockchain database is around 65GB. So you 
should be aiming for a VPS with 100GB storage. Other VPS parameters are 
not critical (1CPU, 1GB RAM is fine). Setup your user to be a 
```sudoer``` and don't call it ```monero``` as we will be setting that 
up specifically for running the node.

You probably want to give your new VPS a hostname by registering it 
with your DNS provider. If you don't have one, you can add your host to 
a billion domains at afraid.org, including moneroworld.com!

## Security first

Make sure you are connecting through ```ssh```. You should disable 
password logins for root (and probably all users) and only use an ssh key 
(this is beyond the scope here - ask your friend how to do this).

Most setups don't have a firewall enabled. Firewalls are a good idea in 
general.

Enable SSH traffic in so you don't kick yourself out:

```
sudo ufw allow ssh
```

And then enable the firewall with

```
sudo ufw enable
```

You can check the status with

```
sudo ufw status
```

## Get Monero

The node software for monero is called ```monerod``` - the monero 
deamon. It is part of the official Monero distribution which can be 
downloaded from the
[Monero Downloads page](https://getmonero.org/downloads/).
We will be working with the **Linux, 64-bit Command-Line Tools Only** 
package.

*Note that you may need the **ARMv8** package if the VPS you selected is 
an ARMv8 model.*

## Download & Verify

```
wget -O monero.tar.bz2 https://downloads.getmonero.org/cli/linux64
sha256sum monero.tar.bz2
```

This will give you the checksum of the download, which you can use to 
verify authenticity by comparing the result to the **SHA256 Hash 
(CLI)** on the
[Monero Downloads page](https://getmonero.org/downloads/).

## Unpack & Install
```
tar xfj monero.tar.bz2
ls -l
```

This shows the folder which was unpacked containing the monero 
applications - at the time of writing we see ```monero-v0.13.0.2```.
Copy the files in there to their final destination:

```
sudo cp monero-v0.13.0.2/* /usr/local/bin
```

Cleanup with

```
rm monero.tar.bz2
rm -r monero-v0.13.0.2
```

## Setup the Service

### Configure the Monero Node

Now we create the configuration for the monero daemon service.

```sudo nano /etc/monerod.conf```

Paste this in there:

```
data-dir=/var/lib/monero
log-file=/var/log/monero/monero.log
log-level=0
no-igd=true
rpc-bind-ip=0.0.0.0
rpc-bind-port=18081
restricted-rpc=true
confirm-external-bind=true
```

Save it with ```^O``` and exit with ```^X```.

This basically tells the ```monerod``` where to store it's data (in 
```/var/lib/monero```) and that it should only accept safe commands so 
you can expose your node to the internet without worrying that people 
will be mining with your node!

### Define the Monero Service

Now we create the service definition for the monero daemon service.

```sudo nano /lib/systemd/system/monerod.service```

Paste this in there & save & exit as before.

```
[Unit]
Description=Monero Full Node
After=network.target

[Service]
User=monero
Group=monero
WorkingDirectory=~
RuntimeDirectory=monero

Type=forking
PIDFile=/run/monero/monerod.pid
ExecStart=/usr/local/bin/monerod --config-file /etc/monerod.conf \
    --detach --pidfile /run/monero/monerod.pid

Restart=always

[Install]
WantedBy=multi-user.target

```

## Setup service user & permissions

Create a new user ```monero``` for running the service. This is overall 
safer than running the service under you working user. You can call 
this user whatever you want, but you would need to change some of the 
commands & configs in this guide to reflect your choice.

```
sudo adduser --system --group monero
```

Create some folders the service needs & set their ownership:

```
# logfile goes here
sudo mkdir /var/log/monero
sudo chown monero.monero /var/log/monero

# blockchain database goes here
sudo mkdir /var/lib/monero
sudo chown monero.monero /var/lib/monero
```

## Run it already!

As we have a firewall set up, we need to enable incoming connections to 
the node:

```
sudo ufw allow 18080
sudo ufw allow 18081
```

Enable the service:

```
systemctl enable monerod
```

And start it!

```
systemctl start monerod
```

If you get errors here - you're doomed! Start off by running

```
sudo -H -u monero /usr/local/bin/monerod --config-file /etc/monerod.conf --pidfile /run/monero/monerod.pid
```

which runs the ```monerod``` as the service would and see what errors 
pop up.

You can watch the daemon doing it's thing by looking at the log:

```
tail -f /var/log/monero/monero.log
```

You can stop this at any time with ```^C```.

## Wait...

Ok, here comes the frustrating part: waiting to sync. Watch the log 
until it says

```
**********************************************************************
You are now synchronized with the network. You may now start monero-wallet-cli.

Use the "help" command to see the list of available commands.
**********************************************************************
```

This may take a few days - you will see progress in the logs though.

## Connect to your shiny new node

Fire up your trusted Monerujo (or other client) and enter your IP or 
hostname in the "Node" field. Open a wallet and enjoy.

## Share

Tell us about your new node on
[/r/Monerujo](https://www.reddit.com/r/Monerujo) or
[/r/Monero](https://www.reddit.com/r/Monero) so others can benefit 
from your fantastic work!

Or change the port of the daemon service to 
```18089``` so that it is automatically included in the 
```node.moneroworld.com``` node pool by changing ```/etc/monerod.conf```:

```
rpc-bind-port=18081
```

to

```
rpc-bind-port=18089
```

and restarting the service:

```
systemctl restart monerod
```

Again, we need to allow this in the firewall:

```
sudo ufw allow 18089
```

And delete the old rule:

```
sudo ufw delete allow 18081
```

If you do this, you will need to add ```:18089``` to the hostname when 
connecting to it (e.g. ```node.moneroworld.com:18089```).

## Upgrading

As the Monero code is ever evolving, you will need to keep it up to 
date. When there is a new version available, you will need to stop the 
service:

```
systemctl stop monerod
```

Then download & deploy as we did above, and then restart the service:

```
systemctl start monerod
```

## Advanced stuff

There are a bunch of other options you can include in the 
```/etc/monerod.conf``` configuration file. Running 
```monerod --help``` will list all commandline options - 
these can be included (one per line) in the configuration file as well!

You may, for example, want to limit the upload speed in case you have a 
data cap: ```limit-rate-up=8192``` (in kB/s).
