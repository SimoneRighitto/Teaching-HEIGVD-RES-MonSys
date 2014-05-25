# Answers, Phase 1

```
# -- INSERT YOUR NAMES HERE -----
Simone, Righitto
Anthony, Roubaty

We certify that we have done all the lab tasks and we have a running environment on our 
machine to prove it. We are ready to demonstrate it at any time and to explain the process
we have followed.
# -------------------------------
```


```
# -- YOUR ANSWER TO QUESTION 1 --
PS C:\Users\RighitZ\Documents\Heig-VD\4semestre\RES\GitHub\Teaching-HEIGVD-RES-MonSys\monsys-web-infra> vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Box 'phusion-open-ubuntu-14.04-amd64' could not be found. Attempting to find and install...
    default: Box Provider: virtualbox
    default: Box Version: >= 0
==> default: Adding box 'phusion-open-ubuntu-14.04-amd64' (v0) for provider: virtualbox
    default: Downloading: https://oss-binaries.phusionpassenger.com/vagrant/boxes/latest/ubuntu-14.04-amd64-vbox.box
    default: Progress: 100% (Rate: 1798k/s, Estimated time remaining: --:--:--)
==> default: Successfully added box 'phusion-open-ubuntu-14.04-amd64' (v0) for 'virtualbox'!
==> default: Importing base box 'phusion-open-ubuntu-14.04-amd64'...
==> default: Matching MAC address for NAT networking...
==> default: Setting the name of the VM: monsys-web-infra_default_1399532851753_72698
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
    default: Adapter 2: hostonly
==> default: Forwarding ports...
    default: 9090 => 8080 (adapter 1)
    default: 22 => 2222 (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection timeout. Retrying...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
==> default: Configuring and enabling network interfaces...
==> default: Mounting shared folders...
    default: /vagrant => C:/Users/RighitZ/Documents/Heig-VD/4semestre/RES/GitHub/Teaching-HEIGVD-RES-MonSys/monsys-web-i
nfra
==> default: Running provisioner: shell...
    default: Running: inline script
==> default: stdin: is not a tty
==> default: Cleaning up Docker containers...
==> default: /tmp/vagrant-shell: line 2: docker: command not found
==> default: /tmp/vagrant-shell: line 3: docker: command not found
==> default: /tmp/vagrant-shell: line 4: docker: command not found
==> default: /tmp/vagrant-shell: line 5: docker: command not found
==> default: /tmp/vagrant-shell: line 6: docker: command not found
==> default: /tmp/vagrant-shell: line 7: docker: command not found
==> default: /tmp/vagrant-shell: line 8: docker: command not found
==> default: /tmp/vagrant-shell: line 9: docker: command not found
==> default: Running provisioner: docker...
    default: Installing Docker (latest) onto machine...
    default: Configuring Docker to autostart containers...
==> default: Building Docker images...
==> default: -- Path: /vagrant/docker/rp-nginx
==> default: -- Path: /vagrant/docker/web-apache
==> default: -- Path: /vagrant/docker/app-nodejs
==> default: Starting Docker containers...
==> default: -- Container: rp-node
==> default: -- Container: web-node-1
==> default: -- Container: web-node-2
==> default: -- Container: app-node
PS C:\Users\RighitZ\Documents\Heig-VD\4semestre\RES\GitHub\Teaching-HEIGVD-RES-MonSys\monsys-web-infra>
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 2 --

PS C:\Users\RighitZ\Documents\Heig-VD\4semestre\RES\GitHub\Teaching-HEIGVD-RES-MonSys\monsys-web-infra> vagrant ssh
Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.13.0-24-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
Last login: Thu May  8 07:58:20 2014 from 10.0.2.2
vagrant@ubuntu-14:~$ uname -a
Linux ubuntu-14 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
vagrant@ubuntu-14:~$

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 3 --

vagrant@ubuntu-14:~$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
heig/rp-nginx       latest              65eb30535221        4 days ago          637.9 MB
heig/app-nodejs     latest              41dcedeac0bb        4 days ago          398.9 MB
heig/web-apache     latest              2ca70c45d584        4 days ago          411.9 MB
<none>              <none>              3e9e5c4aa23b        4 days ago          637.9 MB
dockerfile/ubuntu   latest              cbc81be8f75e        2 weeks ago         378.6 MB
vagrant@ubuntu-14:~$

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 4 --

vagrant@ubuntu-14:~$ docker ps
CONTAINER ID        IMAGE                    COMMAND                CREATED              STATUS              PORTS
            NAMES
155dcf6c5f86        heig/app-nodejs:latest   node /opt/server.js    About a minute ago   Up About a minute   0.0.0.0:7070->80/tcp   app-node
c4ccce596298        heig/web-apache:latest   /usr/sbin/apache2ctl   About a minute ago   Up About a minute   0.0.0.0:8082->80/tcp   web-node-2
4078a4cac91e        heig/web-apache:latest   /usr/sbin/apache2ctl   About a minute ago   Up About a minute   0.0.0.0:8081->80/tcp   web-node-1
f24198982d98        heig/rp-nginx:latest     /opt/init.sh           About a minute ago   Up About a minute   0.0.0.0:9090->80/tcp   rp-node

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 5 --

app-node: "IPAddress": "172.17.0.5"

web-node-2: "IPAddress": "172.17.0.4"

web-node-1: "IPAddress": "172.17.0.3"

rp-node: "IPAddress": "172.17.0.2"

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 6 --

Host (your laptop):
- IP address: 10.192.85.221

Virtual Machine run by Virtual Box
- IP address: 192.168.33.20
- PAT: packets arriving on 10.192.85.221:8080 are forwarded to 192.168.33.20:9090

Docker Bridge
- IP address: 172.17.42.1
- PAT: packets arriving on 172.17.42.1:7070 are forwarded to 172.17.0.5:80
- PAT: packets arriving on 172.17.42.1:8002 are forwarded to 172.17.0.4:80
- PAT: packets arriving on 172.17.42.1:8081 are forwarded to 172.17.0.3:80
- PAT: packets arriving on 172.17.42.1:9090 are forwarded to 172.17.0.2:80

Docker Container 1
- IP address: 172.17.0.5

Docker Container 2
- IP address: 172.17.0.4

Docker Container 3
- IP address: 172.17.0.3

Docker Container 4
- IP address: 172.17.0.2

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 7 --

Which command did you type on the terminal to establish the connection?

telnet 192.168.33.20 9090

What HTTP request did you type and send?

GET / HTTP/1.1
Host: www.monsys.com


What HTTP response did you get?

HTTP/1.1 200 OK
Server: nginx/1.6.0
Date: Thu, 15 May 2014 07:43:12 GMT
Content-Type: text/html
Content-Length: 1584
Connection: keep-alive
X-Powered-By: PHP/5.5.9-1ubuntu4
Vary: Accept-Encoding

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
        "http://www.w3.org/TR/html4/loose.dtd">
<html>
        <head>
                <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
                <link href='http://fonts.googleapis.com/css?family=Terminal+Dosis' rel='stylesheet' type='text/css'>
                <link href='css/main.css' rel='stylesheet' type='text/css'>
                <script type="text/javascript" src="script/jquery-1.6.4.js"></script>
                <title>Welcome To MonSys Front-End</title>

                <script language="JavaScript">

                        $(document).ready(function () {
                                refreshNodes();
                        });

                        function refreshNodes() {
                            $.getJSON('/ajax/resources/nodes',
                            function(data) {
                                var items = [];

                                $.each(data,
                                function(key, val) {
                                    items.push('<li>' + val.name + ", " + val.description + ", load: " + val.currentLoad
Level + ' %</li>');
                                });

                                $('#monitor').html("<ul>" + items.join('') + "</ul>");
                            });
                                var t=setTimeout("refreshNodes()", 1000);
                        }
        </script>
        </head>
        <body>
                <h1>Welcome to MonSys</h1>
                <h2>You are connected to the front-end system, implemented in PHP</h2>
                <b>Note</b>: this page is sending HTTP GET requests to <verbatim>/ajax/resources/nodes</verbatim> in ord
er to retrieve JSON representations of the resources managed by the back-end.
                <p/>

                <div id="monitor">
                        You should monitoring data coming from the back-end here.
                </div>

                <br/>
                Brought to you by the University of Applied Sciences of Western Switzerland
        </body>
</html>

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 8 --

Which command did you type on the terminal to establish the connection?

	telnet www.monsys.com 9090
	

What HTTP request did you type and send?

	GET /ajax/resources/node HTTP/1.1
	Host: www.monsys.com

What HTTP response did you get?

HTTP/1.1 200 OK
Server: nginx/1.6.0
Date: Thu, 22 May 2014 06:46:24 GMT
Content-Type: application/json
Transfer-Encoding: chunked
Connection: keep-alive

fa
[{"name":"P-001","description":"Epson Printer","currentLoadLevel":18.766175769269466},{"name":"P-002","description":"Can
on Printer","currentLoadLevel":38.84145473130047},{"name":"P-003","description":"HP Printer","currentLoadLevel":35.73320
18436864}]
0

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 9 --

What procedure did you follow to validate the configuration of 
your new web nodes? 

Provide details and evidence (command results, etc.) that your 
setup is correct.
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 10 --

What procedure did you follow to validate the configuration of 
your complete infrastructure?

Provide details and evidence (command results, etc.) that your 
setup is correct.

# -------------------------------
```


