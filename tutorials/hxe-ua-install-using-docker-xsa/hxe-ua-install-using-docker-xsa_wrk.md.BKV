---
title: Installing SAP HANA, express edition Server + Apps, with Docker
description: How to install SAP HANA, express edition with XSA on your preferred Docker setup.
primary_tag: products>sap-hana\,-express-edition
tags: [  tutorial>beginner, products>sap-hana\,-express-edition ]
---

## Prerequisites  
 - **Proficiency:** Beginner


## Next Steps
- [How to Install SAP HANA 2.0, express edition Clients](https://www.sap.com/developer/tutorials/hxe-ua-howto-installing-clients.html)
- [How to download and install the HANA Eclipse plugin](https://www.sap.com/developer/tutorials/hxe-howto-eclipse.html)

## Details
### You will learn  
How to install SAP HANA, express edition on your preferred Docker setup.

This tutorial will show you how to install an installation of SAP HANA, express edition with XSA on your Docker installation. This version of SAP HANA, express edition does not contain XSC.

If you wish to install SAP HANA, express edition on a different virtual machine, or you want a custom setup on your Linux machine, see the [Virtual Machine](https://www.sap.com/developer/tutorials/hxe-ua-installing-vm-image.html) or [Binary Method](https://www.sap.com/developer/tutorials/hxe-ua-installing-binary.html) installation guides.

Before you begin, ensure your proxy settings have been properly set up. See [**HTTP/HTTPS proxy**](https://docs.docker.com/engine/admin/systemd/#httphttps-proxy) in the Docker documentation.

### Time to Complete
**10 Min**

---

SAP HANA, express edition is a streamlined version of the SAP HANA platform which enables developers to jump-start application development in the cloud or personal computer to build and deploy modern applications that use up to 32GB memory. SAP HANA, express edition includes the in-memory data engine with advanced analytical data processing engines for business, text, spatial, and graph data - supporting multiple data models on a single copy of the data.

The software license allows for both non-production and production use cases, enabling you to quickly prototype, demo, and deploy next-generation applications using SAP HANA, express edition without incurring any license fees. Memory capacity increases beyond 32GB are available for purchase at the [SAP Store](https://www.sapstore.com/solutions/99055/SAP-HANA%2C-express-edition).

SAP HANA, express edition for Docker has been tested on the following Linux operating system versions:

| Linux OS | OS Version | Docker Editions
| --- | --- | --- |
| `Ubuntu`  | `17.04 (Zesty Zapus)` | [Community](https://store.docker.com/editions/community/docker-ce-server-ubuntu),  [Enterprise](https://store.docker.com/editions/enterprise/docker-ee-server-ubuntu) |
| `openSUSE` | `openSUSE Leap` | [Enterprise](https://store.docker.com/editions/enterprise/docker-ee-server-sles) |
| `CentOS` | `7 (Core)` | [Community](https://store.docker.com/editions/community/docker-ce-server-centos),  [Enterprise](https://store.docker.com/editions/enterprise/docker-ee-server-centos) |
| `Debian` | `9 (Stretch)` | [Community](https://store.docker.com/editions/community/docker-ce-server-debian) |
| `Fedora` | `25 (Server Edition)` | [Community](https://store.docker.com/editions/community/docker-ce-server-fedora) |

**This installation does not support Docker for Windows or Docker for Mac.**

> **Note:**
> These instructions use `openSUSE` and Docker Enterprise Edition as an example. However, any of the supported operating systems listed above are compatible. Use the operating system and Docker installation that fits your needs best.

### (Install Docker)

Download and install the appropriate Docker Edition for your system. Visit the [Docker Community Edition](https://store.docker.com/search?offering=community&type=edition) or [Docker Enterprise Edition](https://store.docker.com/search?offering=enterprise&type=edition) lists for more information and to download Docker for your machine.

> **Note:**
> Ensure your proxy settings have been properly set up. See [**HTTP/HTTPS proxy**](https://docs.docker.com/engine/admin/systemd/#httphttps-proxy) in the Docker documentation.

  

### (Manage Storage System)

If your host file system is `xfs`, you can recommend the storage driver through the `devicemapper` in Docker. Add `-s devicemapper` to the `DOCKER_OPTS` property in the `docker` file.

The minimum recommended storage size is 50G. For example:

```
DOCKER_OPTS="-s devicemapper --storage-opt dm.basesize=50G"
```

For `Ubuntu` and `Debian`, the `DOCKER_OPTS` property can be found at `/etc/default/docker`.

For `Fedora`, `SuSE`, and `Centos`, the `DOCKER_OPTS` property can be found at `/etc/sysconfig/docker`.

Restart the Docker service.

For example, on `SuSE`:

```
sudo systemctl restart docker.service
```

For more information on the storage driver, visit the [Docker storage drivers](https://docs.docker.com/storage/storagedriver/select-storage-driver/) documentation page.

  

### (Log Into Docker)

To log into your Docker account, run:

```bash
sudo docker login
```

Follow the prompts and provide your Docker ID and password.

  

### ((Optional) Test Your Docker Installation)

Test your Docker installation by running the "Hello World" container application. Run the following command from your Docker-enabled command prompt:

```
sudo docker run --name helloWorld alpine echo hello
```

If successful, the following should display:

```
Unable to find image 'alpine:latest' locally
latest: Pulling from library/alpine
88286f41530e: Pull complete
Digest: sha256:<log_number>
Status: Downloaded newer image for alpine:latest
hello
```

If `hello` is printed, you have successfully pulled the container image **alpine** (a demo Linux distribution), and ran the instance of the container `helloWorld`, and ran the command `echo` with an input parameter of `hello`.

If you **did not** get this output, the Docker installation has not been completed or the Docker daemon can not connect to the internet. Review the process and check the [Docker Documentation](https://docs.docker.com/get-started/) for more information in troubleshooting your Docker installation.

Remove the alpine image with the following command:

```bash
sudo docker image rm alpine -f
```

  

### (Download the SAP HANA, express edition Image from the Docker Library)

Go to the [Docker Store](https://store.docker.com/).

Click on the search bar and search for "SAP HANA, express edition".

Choose **SAP HANA, express edition (database and application services)**.

![Docker Store](choose_dockerxsa.png)

HXE 2 SPS 03: https://store.docker.com/images/sap-hana-express-edition-incl-application-services/plans/6e81dee1-5032-4e3a-b227-80175d70eeb5?tab=instructions  

Click on the **Setup Instructions** button.

Copy the Docker pull address. Here is an example:

```bash
sudo docker pull store/saplabs/hanaexpressxsa:2.00.030.00.20180403.2
```
```
2.00.030.00.20180403.2: Pulling from store/saplabs/hanaexpressxsa
1565ab69e5f5: Already exists 
b4908aa94244: Already exists 
4ccb7b4cb9cb: Already exists 
ec1a538ae78e: Already exists 
0f758519f2ae: Already exists 
8d0d7983c9f1: Pull complete 
Digest: sha256:5ec17445d818686d3b7c5d537fac78b0dac136b2f12b544a3db2fb91a0254ef3
Status: Downloaded newer image for store/saplabs/hanaexpressxsa:2.00.030.00.20180403.2

```

Open your Docker-enabled command line and use the Docker pull address to download the image.

This loads the SAP HANA, express edition image. To ensure that the image was loaded successfully, run:

```bash
sudo docker images
```
```
sudo docker image ls
REPOSITORY                     TAG                      IMAGE ID            CREATED             SIZE
store/saplabs/hanaexpressxsa   2.00.030.00.20180403.2   450ddb986d20        2 months ago        24.2GB
store/saplabs/hanaexpress      2.00.030.00.20180403.2   2c1f600d2a72        2 months ago        3GB


```

The SAP HANA, express edition image will be listed as `hanaexpressxsa`.

> **Note:**
> You may have to log into your Docker account to pull the image. From your Docker-enabled command line, run `docker login` and follow the prompts to enter your Docker ID and password. Once you have logged in, try the pull command again.

  


### (Edit the host sysctl.conf file)

Before you can start the container, ensure that the following parameters are set in your host's `/etc/sysctl.conf` file. The host can be a virtual machine, physical machine, or a cloud instance.

```
fs.file-max=20000000
fs.aio-max-nr=262144
vm.memory_failure_early_kill=1
vm.max_map_count=135217728
net.ipv4.ip_local_port_range=60000 65535
```

To edit the `sysctl.conf` file, use the `vi` command to open the file and press `i` to switch to interactive mode. Edit the file as necessary, hit the `esc` key, and type and enter `:wq!` to write and save the changes.

Load the changes by running:

```bash
sudo /sbin/sysctl -p
```

  

### (Edit the /etc/hosts file)

The `hxehost` IP address is private to the installation. In order for applications to access `hxehost`, add the `hxehost` IP address to your machine's hostname map. The hostname map is your machine's **`/etc/hosts`** file. You must edit **`/etc/hosts`** if you want to access any XS Advanced applications or use HANA Cockpit from your machine.

Use the following command:

```bash
sudo sh -c 'echo <hxehost_IP_address>    hxehost >> /etc/hosts'
```

or for `localhost` only setups add `hxehost` as an alias for `localhost`:  
```
# IP-Address    Full-Qualified-Hostname  Short-Hostname  Alias
#

127.0.0.1                                localhost       hxehost
```
  
```
ping hxehost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.029 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.047 ms
```

it may be safer to use an extra local entry within `/etc/hosts` for `hxehost`:  

```
# IP-Address    Full-Qualified-Hostname  Short-Hostname  Alias
#

127.0.0.2       hxehost.localdomain     hxehost
```

### ((Optional) Create a Directory to Persist SAP HANA, express edition Data Outside of the Container)]

Create a directory for the SAP HANA, express edition container and grant it the proper permissions.  

```
mkdir -p /data/<directory_name>
chown 12000:79 /data/<directory_name>
```

The name of this directory does not need to match the name you give to your SAP HANA, express edition container.




### (Set Up Password for SAP HANA, express edition)

To make your system more secure, you specify your own password before you create your container. This is done by creating a `json` file as opposed to having a default password. The file can be stored locally or on another system accessible by URL. If the file is to be stored locally, store it in the */data/<directory_name>* directory you created earlier.

Create the `json` file:

```
vi <file_name>.json
```

Press `i` to start editing and use one of the following formats to create the file:  

```
{
"master_password" : "<password>"
}  
```

or:  

```
{
"system_user_password" : "<password",
"default_tenant_system_user_password" : "<second_password>"
}
```

Here is an example:

```
{
  "master_password" : "SAPhxe123"
}
```

Press `esc` and then enter `wq!` to write and save the file.

This file serves as the master password for your SAP HANA, express edition users. The password must comply with these rules:

* At least 8 characters
* At least 1 uppercase letter
* At least 1 lowercase letter
* At least 1 number
* Can contain special characters, but not _&grave;_ (backtick), _&#36;_ (dollar sign),  _&#92;_ (backslash), _&#39;_ (single quote), or _&quot;_ (double quotation marks).
* Cannot contain dictionary words
* Cannot contain simplistic or systemic values, like strings in ascending or descending numerical or alphabetical order

You must then add permissions for this file to be readable by the `hxeadm` user in the container. Change permissions with:

```
sudo chmod 600 /data/<directory_name>/<file_name>.json
sudo chown 12000:79 /data/<directory_name>/<file_name>.json
```

Be sure to do this with each `json` file you use for your Docker containers.

Make a note of the path to the `json` file. You will need this to load the SAP HANA, express edition container.

  

### (Start SAP HANA, express edition Container)

Use the SAP HANA, express edition image to create a container.

```bash
sudo docker run -p 39013:39013 -p 39015:39015 -p 39041-39045:39041-39045 -p 1128-1129:1128-1129 -p 59013-59014:59013-59014  -p 39030-39033:39030-39033 -p 51000-51060:51000-51060  -p 53075:53075  \
-h hxehost \
-v /data/<directory_name>:/hana/mounts \
--ulimit nofile=1048576:1048576 \
--sysctl kernel.shmmax=1073741824 \
--sysctl net.ipv4.ip_local_port_range='60000 65535' \
--sysctl kernel.shmmni=524288 \
--sysctl kernel.shmall=8388608 \
--name <container_name> \
store/saplabs/hanaexpressxsa:2.00.030.00.20180403.2 \
--agree-to-sap-license \
--passwords-url <file://<path_to_json_file> OR http/https://<url_to_json_file>> \
--proxy-host <proxy_hostname> \
--proxy-port <proxy_port> \
--no-proxy <no_proxy>
```

Example:

```
sudo docker run -p 39013:39013 -p 39015:39015 -p 39041-39045:39041-39045 -p 1128-1129:1128-1129 -p 59013-59014:59013-59014  -p 39030-39033:39030-39033 -p 51000-51060:51000-51060  -p 53075:53075  \
-h hxehost \
-v /data/express_edition:/hana/mounts \
--ulimit nofile=1048576:1048576 \
--sysctl kernel.shmmax=1073741824 \
--sysctl net.ipv4.ip_local_port_range='60000 65535' \
--sysctl kernel.shmmni=524288 \
--sysctl kernel.shmall=8388608 \
--name express_edition \
store/saplabs/hanaexpressxsa:2.00.030.00.20180403.2 \
--agree-to-sap-license \
--passwords-url file:///hana/password.json \
--proxy-host <proxy_hostname> \
--proxy-port <proxy_port> \
--no-proxy <no_proxy>
```

This example creates the SAP HANA, express edition container with the name `express_edition`. This process will take several minutes. The prompt will read `Startup finished` once the container has been successfully running. This container starts in detached mode so you will need to open another command prompt to continue.  


> **Note:**
> If you placed the password file in `/data/<directory_name>/<file_name>.json`, substitute  `file://<path_to_json_file>` with `file:///hana/mounts/<file_name>.json`.

> **Note:**
> Check if the password file `/hana/mounts/<file_name>.json` was deleted after the SAP HANA, express edition container starts.  If not, you can manually delete it. If the `JSON` file you are using is an *http* or *https* URL, you can leave out the `-v` option.

> **Note:**
> Ignore `--proxy-host, --proxy-port, --no-proxy` if you do not have a proxy server.

> **Note:**
> For Linux kernel versions earlier than 4, omit the `net.ipv4.ip_local_port_range` option.

> **Note:**
> for clean HXE shutdowns when a `docker stop` will be issued add a `--stop-timeout` option. E.g. `--stop-timeout 330`. See troubleshooting below.  

```bash
======== Starting HANA container run script ========
Started at: Sun Jul  1 21:22:25 UTC 2018
Script parameters: --agree-to-sap-license --passwords-url file:///hana/mounts/dkhxe203x_pw.json
HANA version: 2.00.030.00.1522210459
Linux kernel version: 4.17
Processing hooks in folder /hana/hooks/system_check ...
Hook candidates:
        /hana/hooks/system_check/100_hxe_check_system_prerequisites
Executing hook /hana/hooks/system_check/100_hxe_check_system_prerequisites ...
        Checking /proc/sys prerequisites ...
                ok: /proc/sys/kernel/shmmax: 1073741824>=1073741824
                ok: /proc/sys/kernel/shmmni: 524288>=4096
                ok: /proc/sys/kernel/shmall: 8388608>=8388608
                ok: /proc/sys/fs/file-max: 20000000>=20000000
                ok: /proc/sys/fs/aio-max-nr: 262144>=131072
                ok: /proc/sys/vm/memory_failure_early_kill: 1
                ok: /proc/sys/vm/max_map_count: 135217728>=2048576
                ok: /proc/sys/net/ipv4/ip_local_port_range: 60000>=40000
        Check succeeded: /proc/sys prerequisites
        Checking limits ...
                ok: max number of open file descriptors (ulimit -n): 1048576>=1048576
        Check succeeded: limits
Execution of hook /hana/hooks/system_check/100_hxe_check_system_prerequisites finished (exit code 0)
Finished execution of hooks in folder /hana/hooks/system_check
Checking version compatibility ...
Downloading password file from file:///hana/mounts/dkhxe203x_pw.json ...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    37  100    37    0     0   860k      0 --:--:-- --:--:-- --:--:--  860k
Deleting local password file: /hana/mounts/dkhxe203x_pw.json
Entering pre start initialization phase ...
Creating consistency check files ...
Processing hooks in folder /hana/hooks/pre_start_init ...
Hook candidates:
        /hana/hooks/pre_start_init/010_license_agreement
        /hana/hooks/pre_start_init/010_license_agreement.json (ignored, not an executable regular file)
Hook /hana/hooks/pre_start_init/010_license_agreement requires parameters: AGREE_TO_SAP_LICENSE
Executing hook /hana/hooks/pre_start_init/010_license_agreement ...
        License agreement check succeeded (AGREE_TO_SAP_LICENSE=true)
Execution of hook /hana/hooks/pre_start_init/010_license_agreement finished (exit code 0)
Finished execution of hooks in folder /hana/hooks/pre_start_init
Entering pre start phase ...
Processing hooks in folder /hana/hooks/pre_start ...
Hook candidates:
        (no executable files detected)
Finished execution of hooks in folder /hana/hooks/pre_start
Change hardware key...
nameserver hxehost:39001 not responding.
Opening persistence ...
run as transaction master

converting topology from cloned instance...
- keeping instance 90
- keeping host hxehost
done.
Finished pre start sequence
Starting up HANA server...
Impromptu CCC initialization by 'rscpCInit'.
  See SAP note 1266393.


StartService
OK
OK
Starting instance using: /usr/sap/HXE/SYS/exe/hdb/sapcontrol -prot NI_HTTP -nr 90 -function StartWait 2700 2


01.07.2018 21:22:42
Start
OK

01.07.2018 21:26:08
StartWait
FAIL: process hdbxscontroller HDB XS Controller not running

```

This seems to be a not uncommon problem with the 201804xx image.  
Remedy see step 6 from these troubleshooting steps:  
https://blogs.sap.com/2018/07/02/getting-hxe-xsa-serverapps-on-docker-to-work-for-you/  

Repairing steps:  

Build the container with the `--dont-exit-on-error` parameter. Then after the failure the container is still alive

```
...
04.07.2018 23:00:40
StartWait
FAIL: process hdbxscontroller HDB XS Controller not running
Exit trap called with exit code 2
Removing trap for signal EXIT ...
Resetting traps for signals QUIT INT TERM HUP (can be used to unblock) ...
Keeping container alive. Start process 1 will block now ...
In order to inspect call:  docker exec -ti <container> /bin/bash
In order to unblock call:  docker stop <container>  OR  docker kill -s TERM <container>  
```



and can be maintained with:  

  
`sudo docker exec -it DKHXE203X bash`  
  
```
hxeadm@hxehost:/usr/sap/HXE/HDB90> HDB info
USER       PID  PPID %CPU    VSZ   RSS COMMAND
hxeadm    2011     0  0.0  21056  4084 bash
hxeadm    2395  2011 22.2  20256  3316  \_ /bin/sh /usr/sap/HXE/HDB90/HDB info
hxeadm    2426  2395  0.0  43532  3416      \_ ps fx -U hxeadm -o user,pid,ppid,pcpu,vsz,rss,args
hxeadm       1     0  0.0  20916  3780 /bin/bash /run_hana --agree-to-sap-license --passwords-url file:///hana/mounts/dkhxe203x_pw.json
hxeadm     280     1  0.0  20128  3060 /bin/sh /usr/sap/HXE/HDB90/HDB start
hxeadm     340   280  0.0  32872 11972  \_ /usr/sap/HXE/SYS/exe/hdb/sapcontrol -prot NI_HTTP -nr 90 -function StartWait 2700 2
hxeadm     328     1  0.5 502564 33228 /usr/sap/HXE/HDB90/exe/sapstartsrv pf=/usr/sap/HXE/SYS/profile/HXE_HDB90_hxehost -D -u hxeadm
hxeadm     404     1  0.0  23720  2896 sapstart pf=/usr/sap/HXE/SYS/profile/HXE_HDB90_hxehost
hxeadm     412   404  1.0 224400 55656  \_ /usr/sap/HXE/HDB90/hxehost/trace/hdb.sapHXE_HDB90 -d -nw -f /usr/sap/HXE/HDB90/hxehost/daemon.ini pf=/usr/sap/HXE/SY
hxeadm     429   412 19.6 3836712 2190876      \_ hdbnameserver
hxeadm     578   412  2.2 1322656 337648      \_ hdbcompileserver
...
```

repair:  
```
cd /hana/shared/HXE/xs/app_working/stager/
hxeadm@hxehost:/hana/shared/HXE/xs/app_working/stager> ls -al
total 28
drwx--x--x 6 hxeadm sapsys 4096 Apr  4 21:52 .
drwxr-xr-x 1 hxeadm sapsys 4096 Jul  4 23:00 ..
drwx------ 5 hxeadm sapsys 4096 Apr  4 21:52 cache
drwx------ 2 hxeadm sapsys 4096 Apr  4 21:52 home
drwx------ 3 hxeadm sapsys 4096 Apr  4 21:52 tmp
drwx------ 2 hxeadm sapsys 4096 Apr  4 21:52 work
hxeadm@hxehost:/hana/shared/HXE/xs/app_working/stager> rm -rf *
hxeadm@hxehost:/hana/shared/HXE/xs/app_working/stager> ls
hxeadm@hxehost:/hana/shared/HXE/xs/app_working/stager> exit
exit
```

stop the still alive container:  
`sudo docker stop -t 200 DKHXE203X`  


```
Start process unblocked ...
Exiting now with original exit code (2) ...
```

`sudo docker start DKHXE203X`

now the initialisation will continue and after some wait the container will be up and healthy.
```
55c95dec12fc        store/saplabs/hanaexpressxsa:2.00.030.00.20180403.2   "/run_hana --agree..."   33 minutes ago      Up 2 minutes (healthy)
```  

### (Log into SAP HANA, express edition Container)

To start your SAP HANA, express edition container, run the following command:

```bash
sudo docker exec -it <container_name> bash
```

Example:

```
sudo docker exec -it express_edition bash
```

#### troubleshooting  

https://blogs.sap.com/2017/07/04/xsa-installation-issues-and-troubleshooting/  
  
based on this discussion: https://answers.sap.com/questions/539188/hxe-server-apps-on-docker-not-able-to-start-contai.html  

### ((Optional) Test the Container)

When you are logged into the SAP HANA, express edition container, you can test your installation by entering the following:

```bash
whoami
```

You should be logged in as `hxeadm`, the default SAP HANA, express edition user.

You can also enter the following:

```bash
HDB info
```

And you should see the following services running:

* `hdbnameserver`
* `hdbcompileserver`
* `hdbdiserver`
* `hdbwebdispatcher`

  

### ((Optional) Log Into System or Tenant Database)

You can log into the system database with the following command:

```bash
hdbsql -i 90 -d <system_database> -u SYSTEM -p <password>
```

You can log into your tenant database with the following command:

```bash
hdbsql -i 90 -d <tenant_database> -u SYSTEM -p <password>
```

__JDBC__

---

To log into your system database via JDBC, use the following command:

```bash
jdbc:sap://<ip_address>:39013/databaseName=<database_name>
```

To log into your tenant database via JDBC, use the following command:

```bash
jdbc:sap://<ip_address>:39015/databaseName=<tenant_name>
```

  

### ((Optional) Test SAP Web IDE)

After you have logged in, view the list of XSA applications. Enter:

```bash
xs apps
```

> **Note:**
> When you run the `xs apps` command for the first time, it may take 1-2 minutes for the system to return the list of XSA applications.

Check that the application `webide` shows `STARTED` in the list of XSA applications, and has 1/1 instances. (If the list shows 0/1 in the instance column, the application is not started.)

> **Note:**
> Normally it only takes a few minutes for XSA services to start. However. depending on your machine, it can take over 30 minutes for XSA services to begin. If the service doesn't show `STARTED` and doesn't show `1/1` instances, keep waiting until the service is enabled.

Make a note of the URL for `webide`.

![loio5edd67a000a745cdb47d3a00973d0632_HiRes](loio5edd67a000a745cdb47d3a00973d0632_HiRes.png)

> **Note:**
> The command `xs apps | grep webide` returns the `webide` row only.


`hxeadm@hxehost:/usr/sap/HXE/HDB90>  xs apps  `
```
FAILED: Could not refresh auth token: The token expired, was revoked, or the token ID is incorrect
TIP: Try using 'xs login' to log in again.
```
`hxeadm@hxehost:/usr/sap/HXE/HDB90>  xs login  `
```
API_URL: https://hxehost:39030
USERNAME: XSA_ADMIN
PASSWORD> 
Authenticating...
Authentication failed: User must change password. Login at 'https://hxehost:39032/uaa-security' to change the password.  
```
do so  

`hxeadm@hxehost:/usr/sap/HXE/HDB90>  xs apps  `
```
Not logged in. Use 'xs login' to log in.
```
`hxeadm@hxehost:/usr/sap/HXE/HDB90>  xs login  `
```
API_URL: https://hxehost:39030
USERNAME> XSA_ADMIN
PASSWORD> 
Authenticating...
ORG: HANAExpress

Existing spaces: 
0.      development
1.      SAP
SPACE> 1
SPACE: SAP
API endpoint:   https://hxehost:39030 (API version: 1)
User:           XSA_ADMIN
Org:            HANAExpress
Space:          SAP
```
`hxeadm@hxehost:/usr/sap/HXE/HDB90>  xs apps  `
```
Getting apps in org "HANAExpress" / space "SAP" as XSA_ADMIN...
Found apps: 
                                                                                    
name                          requested state   instances   memory    disk          urls
---------------------------------------------------------------------------------------------------------
auditlog-db                   STOPPED           0/1         16.0 MB   <unlimited>   <none>
auditlog-server               STARTED           1/1         256 MB    <unlimited>   https://hxehost:51002
auditlog-broker               STARTED           1/1         64.0 MB   <unlimited>   https://hxehost:51003
deploy-service                STARTED           1/1         280 MB    <unlimited>   https://hxehost:51004
component-registry-db         STOPPED           0/1         16.0 MB   <unlimited>   <none>
product-installer             STARTED           1/1         256 MB    <unlimited>   https://hxehost:51005
auditlog-odata                STARTED           1/1         128 MB    <unlimited>   https://hxehost:51007
...
```

same change user password for user `XSA_DEV` on https://hxehost:39032/uaa-security  

Test your Web IDE connection. Enter the URL for Web IDE in a web browser.

```
Example: https://hxehost:53075
```

Log on to Web IDE using the `XSA_DEV` user and the password you made during installation.

If you are prompted to change your password, follow the instructions.

  

[Docker Run Usage: ](-Help Command)

The following is a list of options available for the `sudo docker run store/saplabs/hanaexpressxsa` command.

```
docker run store/saplabs/hanaexpressxsa:2.00.030.00.20180403.2 -h
usage: [options]

--dont-check-consistency           Skip consistency check between mount points
--dont-check-mount-points          Skip check for allowed mount points
--dont-check-version               Skip compatibility check of current and last HANA version
--dont-check-system                Skip check for incompatible /proc/sys values
--dont-exit-on-error               Halt script on error to allow root cause analysis
                                   (MUST NOT be used in production)
--license-url <url>                URL for a license file (json)
                                   Format: {"landscape-id":"<8-4-4-4-12 GUID>", "license":"<license>"}
--passwords-url <url>              URL for a password file (json). Format:
                                       {"master_password":"<pwd>"}
                                   or
                                       {"system_user_password":"<pwd>","default_tenant_system_user_password":"<pwd>"}
--proxy-host                       Proxy host name
--proxy-host                       Proxy port number
--no-proxy                         Comma separated list of hosts/domains that do not need proxy

--agree-to-sap-license             Indicates you agree to the SAP Developer Center Software Developer License Agreement.
```

  
[](Issues)  

after a sleep of the host the container does not properly wake up. E.g.:  
`xs apps`
unresponsive for minutes with 100% load on all CPU cores. When issuing a `docker stop -t 200` it is only force stopped after 200 secs, no clean shutdown.  
```
FAILED to communicate with XS Controller:
Error executing request GET https://hxehost:39030/v2/spaces/d426399b-aa98-4a73-ae38-efb52b31dcf1: java.net.SocketTimeoutException: Read timed out (local port 61930 to address 172.17.0.2 (hxehost), remote port 39030 to address 172.17.0.2 (hxehost))
```

or

`top -d 10`
```
top - 08:57:40 up 1 day, 10:09,  0 users,  load average: 167.38, 95.04, 39.97
Tasks:  49 total,   2 running,  47 sleeping,   0 stopped,   0 zombie
%Cpu(s): 37.4 us,  9.1 sy,  0.1 ni, 48.4 id,  0.2 wa,  0.0 hi,  4.9 si,  0.0 st
KiB Mem:  32660532 total, 32120948 used,   539584 free,  1530036 buffers
KiB Swap: 33554428 total,    82244 used, 33472184 free. 12205336 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND  
  600 hxeadm    20   0 4887336 3.157g 419748 S 316.0 10.14  17:22.41 hdbindexserver  
  429 hxeadm    20   0 6151848 4.289g 417904 S 268.0 13.77  15:58.50 hdbnameserver  
  579 hxeadm    20   0 1325792 367152 174784 S 64.00 1.124   3:14.93 hdbcompileserve  
  758 hxeadm    20   0 1539468 556580 171968 S 64.00 1.704   3:15.87 hdbwebdispatche  
  756 hxeadm    20   0 1332492 341876 170800 S 56.00 1.047   2:52.09 hdbdiserver  
  412 hxeadm    20   0  224420  56964  44272 R 8.000 0.174   0:23.07 hdb.sapHXE_HDB9  
```

`HDB stop`
```
hdbdaemon will wait maximal 300 seconds for NewDB services finishing.
Stopping instance using: /usr/sap/HXE/SYS/exe/hdb/sapcontrol -prot NI_HTTP -nr 90 -function Stop 400

06.07.2018 08:59:53
Stop
OK
Waiting for stopped instance using: /usr/sap/HXE/SYS/exe/hdb/sapcontrol -prot NI_HTTP -nr 90 -function WaitforStopped 600 2


06.07.2018 09:09:54
WaitforStopped
FAIL: Timeout
```

`sudo docker attach DKHXE203X`

```
^CReceived signal: INT
Removing trap for signal EXIT ...
Ignoring signals: QUIT INT TERM HUP ...
Stopping HANA ...
hdbdaemon will wait maximal 300 seconds for NewDB services finishing.
Stopping instance using: /usr/sap/HXE/SYS/exe/hdb/sapcontrol -prot NI_HTTP -nr 90 -function Stop 400

06.07.2018 09:22:07
Stop
OK
Waiting for stopped instance using: /usr/sap/HXE/SYS/exe/hdb/sapcontrol -prot NI_HTTP -nr 90 -function WaitforStopped 600 2


06.07.2018 09:22:07
WaitforStopped
OK
hdbdaemon still running, wait more...
hdbdaemon has stopped now.
Waiting for shutdown procedure to finish ...

06.07.2018 09:22:08
WaitforStopped
OK
Stopping sapstartsrv ...

06.07.2018 09:22:08
StopService
OK
Shutdown procedure finished ...
Calling HANA info on exit ...
USER       PID  PPID %CPU    VSZ   RSS COMMAND
hxeadm   14632     0  0.0  21056  4128 bash
hxeadm       1     0  0.0  20916  3828 /bin/bash /run_hana --agree-to-sap-license --passwords-url file:///hana/mounts/dkhxe203x_pw.json --dont-exit-on-error
hxeadm   18141     1 36.3  20124  3076 /bin/sh /usr/sap/HXE/HDB90/HDB info
hxeadm   18194 18141  0.0  43532  3404  \_ ps fx -U hxeadm -o user,pid,ppid,pcpu,vsz,rss,args
That's it! Bye.
Terminating with exit code 129
Terminated at: Fri Jul  6 09:22:10 UTC 2018
```

Restart of the container fails thereafter.  

`sapstartsrv.log` is here: `/hana/shared/HXE/HDB90/hxehost/trace/sapstartsrv.log`

`stdout2`:  
```
An instance of this service is already running.
You should consider checking if the process with the id 413 is running
and of type hdbdaemon. If you are sure that there is no instance alive
remove the file /usr/sap/HXE/HDB90/hxehost/lock/hdbdaemon@39000.pid
and restart.
```

deleting the `.pid` was enough to get the container going again with a `docker start ...`  

similar endless loop after host hibernate:  
```
top - 12:08:51 up  2:15,  0 users,  load average: 161.77, 161.72, 154.32
Tasks:  73 total,   3 running,  70 sleeping,   0 stopped,   0 zombie
%Cpu(s): 83.9 us,  1.7 sy,  0.1 ni, 13.7 id,  0.1 wa,  0.0 hi,  0.5 si,  0.0 st
KiB Mem:  32660532 total, 15258816 used, 17401716 free,   139548 buffers
KiB Swap: 33554428 total,  4147928 used, 29406500 free.  2389192 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND    
  599 hxeadm    20   0 4681576 1.065g  12876 S 326.7 3.418 145:00.46 hdbindexs+ 
  429 hxeadm    20   0 6281448 3.054g  13044 R 286.7 9.806 145:43.35 hdbnamese+ 
  816 hxeadm    20   0 1538252 382676   4796 S 66.67 1.172  30:43.09 hdbwebdis+ 
  814 hxeadm    20   0 1331532 159004   2376 S 60.00 0.487  26:00.56 hdbdiserv+ 
  578 hxeadm    20   0 1324832  44952   4316 S 53.33 0.138  30:43.57 hdbcompil+ 
  412 hxeadm    20   0  224420   5448   4884 R 6.667 0.017   4:42.67 hdb.sapHX+ 
```
even when the container had been `docker pause`d thru the hibernate time!?  


workaround by executing a `docker stop` at suspend/hibernate (may be needed for shutdown too)
see: https://blog.christophersmart.com/2016/05/11/running-scripts-before-and-after-suspend-with-systemd/  
realized here in: `/usr/lib/systemd/system-sleep/docker.sleep`  
```bash
...
  docker ps  | awk '/hanaexpress/{print $1}' | xargs -r -n1 docker stop -t  330  >> /tmp/systemd_suspend_test
...
```
a hana container, while starting does not seem to allow to be stoped by ignoring signals.  


Same for a graceful container stop at host shutdown:  
service:  
`/usr/lib/systemd/system/dockerShutdownHANA.service`  
script:  
`/usr/local/sbin/dockerShutdownHANA`  

alternative for graceful container shutdown at host shutdown: (?)  
use the `--stop-timeout` parameter when the instance is created and set it to e.g. 330 s.

## Next Steps
- [How to Install SAP HANA 2.0, express edition Clients](https://www.sap.com/developer/tutorials/hxe-ua-howto-installing-clients.html)
- [Download and Install the HANA Eclipse plugin](https://www.sap.com/developer/tutorials/hxe-howto-eclipse.html)
