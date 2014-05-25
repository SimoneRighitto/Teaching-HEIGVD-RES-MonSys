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

Here we start vagrant:

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

First of all we find out the containers runninf with:

	vagrant@ubuntu-14:~$ docker ps -a
	
	
CONTAINER ID        IMAGE                    COMMAND                CREATED             STATUS              PORTS
           NAMES
749c1ceb155d        heig/web-clash:latest    /usr/sbin/apache2ctl   22 minutes ago      Up 22 minutes       0.0.0.0:8085
->80/tcp   web-clash-3
f4d585c8a48c        heig/web-clash:latest    /usr/sbin/apache2ctl   22 minutes ago      Up 22 minutes       0.0.0.0:8084
->80/tcp   web-clash-2
2122cce42728        heig/web-clash:latest    /usr/sbin/apache2ctl   22 minutes ago      Up 22 minutes       0.0.0.0:8083
->80/tcp   web-clash-1
eb882d86441a        heig/app-nodejs:latest   node /opt/server.js    22 minutes ago      Up 22 minutes       0.0.0.0:7070
->80/tcp   app-node
028df1287d5e        heig/web-apache:latest   /usr/sbin/apache2ctl   22 minutes ago      Up 22 minutes       0.0.0.0:8082
->80/tcp   web-node-2
6db572ed8d1e        heig/web-apache:latest   /usr/sbin/apache2ctl   22 minutes ago      Up 22 minutes       0.0.0.0:8081
->80/tcp   web-node-1
6827f4bda4e2        heig/rp-nginx:latest     /opt/init.sh           22 minutes ago      Up 22 minutes       0.0.0.0:8014
->80/tcp   rp-node

Then we have inspected the 3 containers to get informations:

	docker inspect web-clash-1
	docker inspect web-clash-2
	docker inspect web-clash-3
	
and we get the following informations:

	web-clash-1 : IP 172.17.0.6 Port: 80803
	web-clash-2 : IP 172.17.0.7 Port: 80804
	web-clash-3 : IP 172.17.0.8 Port: 80805
	
	
then we ping the 3 containers to see if they are alive:

vagrant@ubuntu-14:~$ ping 172.17.0.6
PING 172.17.0.6 (172.17.0.6) 56(84) bytes of data.
64 bytes from 172.17.0.6: icmp_seq=1 ttl=64 time=0.121 ms
64 bytes from 172.17.0.6: icmp_seq=2 ttl=64 time=0.158 ms
64 bytes from 172.17.0.6: icmp_seq=3 ttl=64 time=0.120 ms
64 bytes from 172.17.0.6: icmp_seq=4 ttl=64 time=0.141 ms
64 bytes from 172.17.0.6: icmp_seq=5 ttl=64 time=0.115 ms
♥
--- 172.17.0.6 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 0.115/0.131/0.158/0.016 ms


}]vagrant@ubuntu-14:~ping 172.17.0.7
PING 172.17.0.7 (172.17.0.7) 56(84) bytes of data.
64 bytes from 172.17.0.7: icmp_seq=1 ttl=64 time=0.195 ms
64 bytes from 172.17.0.7: icmp_seq=2 ttl=64 time=0.065 ms
64 bytes from 172.17.0.7: icmp_seq=3 ttl=64 time=0.120 ms
64 bytes from 172.17.0.7: icmp_seq=4 ttl=64 time=0.153 ms
♥
--- 172.17.0.7 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.065/0.133/0.195/0.048 ms

vagrant@ubuntu-14:~$ ping 172.17.0.8
PING 172.17.0.8 (172.17.0.8) 56(84) bytes of data.
64 bytes from 172.17.0.8: icmp_seq=1 ttl=64 time=0.368 ms
64 bytes from 172.17.0.8: icmp_seq=2 ttl=64 time=0.359 ms
64 bytes from 172.17.0.8: icmp_seq=3 ttl=64 time=0.147 ms
64 bytes from 172.17.0.8: icmp_seq=4 ttl=64 time=0.105 ms
♥
--- 172.17.0.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3008ms
rtt min/avg/max/mdev = 0.105/0.244/0.368/0.121 ms
 



# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 10 --

What procedure did you follow to validate the configuration of 
your complete infrastructure?

Provide details and evidence (command results, etc.) that your 
setup is correct.

After having modified nginx configurations we have done the following test

1. a simple HTTP GET request to the server directly from the virtual machine
	vagrant@ubuntu-14:~$ telnet 172.17.0.6 80
	Trying 172.17.0.6...
	Connected to 172.17.0.6.
	Escape character is '^]'.
	GET / HTTP/1.1
	Host: www.live.clashofclasses.ch

And this give us the following response:

	HTTP/1.1 200 OK
	Date: Sun, 25 May 2014 09:13:15 GMT
	Server: Apache/2.4.7 (Ubuntu)
	Last-Modified: Thu, 15 May 2014 06:49:22 GMT
	ETag: "80a-4f96ab26a4080"
	Accept-Ranges: bytes
	Content-Length: 2058
	Vary: Accept-Encoding
	Content-Type: text/html

	<!DOCTYPE html>
	<html lang="en">
	  <head>
		<meta charset="utf-8">
		<meta http-equiv="X-UA-Compatible" content="IE=edge">
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<meta name="description" content="">
		<meta name="author" content="">
			<link href="http://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-awesome.css" rel="stylesheet">
		<title>Sticky Footer Template for Bootstrap</title>

		<!-- Bootstrap core CSS -->
		<link href="./css/live-bootstrap.css" rel="stylesheet">

		<!-- Custom styles for this template -->
		<link href="./css/sticky-footer.css" rel="stylesheet">

		<!-- Just for debugging purposes. Don't actually copy this line! -->
		<!--[if lt IE 9]><script src="../../assets/js/ie8-responsive-file-warning.js"></script><![endif]-->

		<!-- HTML5 shim and Respond.js IE8 support of HTML5 elements and media queries -->
		<!--[if lt IE 9]>
		  <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
		  <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
		<![endif]-->
	  </head>

	  <body>

		<!-- Begin page content -->
		<div class="container">
		  <div class="page-header">
			<h1>Welcome To Clash of Classes!</h1>
		  </div>
		  <p class="lead">This is the Welcome Page for the <b>live</b> section of the website, which is accessible at this U
	RL <a href="http://live.clashofclasses.ch">http://live.clashofclasses.ch</a>.</p>
		  <p class="lead">You can jump to the <b>dashboard</b> section of the website <a href="http://dashboard.clashofclass
	es.ch">here</a>.</p>

			<p></p>
					<img src="success.jpg" width="300">
			<p></p>


		</div>


		<div id="footer">
		  <div class="container">
			<p class="text-muted">We <i class="fa fa-heart"></i> Application Level Protocols</p>
		  </div>
		</div>


		<!-- Bootstrap core JavaScript
		================================================== -->
		<!-- Placed at the end of the document so the pages load faster -->
	  </body>
	</html>
	
2. The same as 1 but for the www.leaderboard.clashofclasses.ch

	vagrant@ubuntu-14:~$ telnet 172.17.0.7 80
	Trying 172.17.0.7...
	Connected to 172.17.0.7.
	Escape character is '^]'.
	GET / HTTP/1.1
	Host: www.leaderboard.clashofclasses.ch
	
And here is the answer:

	<!DOCTYPE html>
	<html lang="en">
	  <head>
		<meta charset="utf-8">
		<meta http-equiv="X-UA-Compatible" content="IE=edge">
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<meta name="description" content="">
		<meta name="author" content="">
			<link href="http://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-awesome.css" rel="stylesheet">
		<title>Sticky Footer Template for Bootstrap</title>

		<!-- Bootstrap core CSS -->
		<link href="./css/dashboard-bootstrap.css" rel="stylesheet">

		<!-- Custom styles for this template -->
		<link href="./css/sticky-footer.css" rel="stylesheet">

		<!-- Just for debugging purposes. Don't actually copy this line! -->
		<!--[if lt IE 9]><script src="../../assets/js/ie8-responsive-file-warning.js"></script><![endif]-->

		<!-- HTML5 shim and Respond.js IE8 support of HTML5 elements and media queries -->
		<!--[if lt IE 9]>
		  <script src="https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js"></script>
		  <script src="https://oss.maxcdn.com/libs/respond.js/1.4.2/respond.min.js"></script>
		<![endif]-->
	  </head>

	  <body>

		<!-- Begin page content -->
		<div class="container">
		  <div class="page-header">
			<h1>Clash of Classes Dashboard</h1>
		  </div>
		  <p class="lead">This is the Welcome Page for the <b>dashboard</b> section of the service, which is accessible at t
	his URL <a href="http://dashboard.clashofclasses.ch">http://dashboard.clashofclasses.ch</a></p>
		  <p class="lead">You can go back to the <b>live</b> section <a href="http://live.clashofclasses.ch">here</a>.</p>

	<p></p>
			<img src="kid.jpg" width="300">
	<p></p>



		</div>

		<div id="footer">
		  <div class="container">
			<p class="text-muted">We <i class="fa fa-heart"></i> Application Level Protocols Teachers</p>
		  </div>
		</div>


		<!-- Bootstrap core JavaScript
		================================================== -->
		<!-- Placed at the end of the document so the pages load faster -->
	  </body>
	</html>

	
And from the local browser:

<center><img width=520 src="screenshot/live.png"></center>

<center><img width=520 src="screenshot/leaderboard.png"></center>
	


# -------------------------------
```


