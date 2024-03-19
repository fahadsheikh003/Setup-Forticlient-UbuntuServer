# Steps to install and setup Forticlient on Ubuntu Server

First download the Fortigate SSLVPN CLI

```
wget https://github.com/fahadsheikh003/Setup-Forticlient-UbuntuServer/blob/main/forticlientsslvpn_linux_4.4.2328.tar.gz
```

You need to uncompress the downloaded file:

```
tar -xzvf forticlientsslvpn_linux_4.4.2328.tar.gz
```

Install ppp (in case you don't have it):

```
sudo apt-get install ppp
```

Go to the installer setup dir:

```
cd ./forticlientsslvpn/64bit/helper
```

and run the setup file:

```
sudo ./setup.linux.sh
```

go to the following dir

```
cd  forticlientsslvpn/64bit/
```

Finally you can connect whenever you want using this command:

```
./forticlientsslvpn_cli --server serveraddress:port --vpnuser username
```

For automation, Install expect (in case you don't have it):

```
sudo apt-get install expect
```

Sample Expect Script to auto connect to Forticlient
```
#!/usr/bin/expect -f

match_max 1000000
set timeout -1

spawn /home/user/forticlientsslvpn/64bit/forticlientsslvpn_cli --server serveraddress:port --vpnuser username
expect "Password for VPN:"
send "Password
"

expect "Would you like to connect to this server? (Y/N)"
send "Y
"

interact
```