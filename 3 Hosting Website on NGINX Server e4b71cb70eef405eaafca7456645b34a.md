# 3. Hosting Website on NGINX Server

In this project I will deploy a website on the `NIGIX server` 

# STEP 1 (Checking System Information):

- I have started and fired up my `Linux Machine` and now i will run some basic command to learn about the `username` `current working directory` `hostname` `operating system info and details`

```bash
whoami   #Current user name information
pwd                       # Print the currentt directory in which you are working     
hostname                  # The hostname of your machine
cat /etc/os-release       # Detail information about your operating system 
cat /etc/redhat-release   # Full name of your current OS
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled.png)

- It gives me following information
    - user = root
    - pwd = /root
    - hostname = www.talha.com
    - `cat /etc/os-release`  = Rocky Linux version 9.3 with version 9.3 and etc.
    - `cat /etc/redhat-release` = Rocky Linux release 9.3
- I want to change the `hostname` name to [`www.nginixproject.com`](http://www.nginixproject.com) . I will run the command

```bash
hostnamectl set-hostname www.nginixproject.com  #This will change the hostanme to `www.nginixproject.com`

# To verify i will run the command `hostname`
hostname
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%201.png)

- It is always a good practice to know about the `ip address` of the machine you are using. Run the following command

```bash
ifconfig
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%202.png)

The current `ip address` of the machine is `192.168.1.10`

# Step 2 (Updating OS and Installing Nginx):

### Checking system updates and installing:

- It is a good practice to keep your `operating system` up to date. before doing any project or make it a `scheduled task` to check it periodically.
- We will first of all check is there any `updates` available for our current OS

```bash
	dnf check-update  # A list of available updates for OS will be given if any update available
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%203.png)

We have a lot of updates available.

- To make the update we run the command

```bash
dnf update -y  # This is automatically startt updating our OS
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%204.png)

We have to download and install a total of `1.2G` update. Because we have used `-y` while running the command , it automatically started to download.

- After the downloading and installation of the the update. A `complete message` will be displayed

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%205.png)

or you can check it again by running the command `dnf update`

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%206.png)

## Installing `Nginx Server`

- After we have completed our `system OS update` . We can now install `Nginx Server`.
- First of all we will check either it is already installed on our machine by running the `rpm` command :

```bash
 rpm -qa | grep nginx
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%207.png)

No message was returned this shows that , there is no `NGINX` is installed on it.

- To download and install the `nginx package` along with its other `dependencies` we will run the command :

```bash
dnf install -y nginx* # Using -y will install the package without promt.
											# wildcard will install the dependencies as well
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%208.png)

The package is installed to double check we can again run the command `rpm -qa | grep nginx`

- We can also check the `version of nginx` which will also confirm its installation to our machine using the command `nginx -v`

```bash
nginx -v
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%209.png)

- We also need to have package name `openSSL` and `mod_ssl` which will help us in generating keys if we want to install the `SSL/TLS` certificate for our website.
- We can check the package using the command:

```bash
rpm -qa | grep openssl
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2010.png)

The image shows that the packages are installed already. If they are installed we should have installed them using the command :

```bash
dnf install openssl
dnf install mod_ssl
```

- Now `start` the `nginx server` , run the command:

```bash
systemctl start nginx

```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2011.png)

if there is no message it means that the `service has been started`. It can be checked using the command 

```bash
systemctl status nginx
```

 

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2012.png)

The `nginx` is activated. But if you look closely in the `3rd line` the `service is disabled` 

- To enable the service of nginx , and to make it automatically start when we run our machine again we will execute the following command:

```bash
systemctl enable nginx.service --now  #
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2013.png)

# Step 3 (Testing The Nginx Server):

- In order to test the `nginix` we have few commands . First we will check either the `configuration` of the `nginix` is okay or have some issues and also test it using the command `nginx -t`:

```bash
nginix -t
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2014.png)

- If we want to view the detail information and also wanted to print it we can use the command `nginx -T`
- -In order to view `all the command` associated with nginx and their functions we run the command `nginx -h`

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2015.png)

- We can `check and test` the nginx on our `web browser` by entering the `ip address` as we seen above the `ip address` of our machine is `192.168.1.10`

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2016.png)

This shows that the `ngnix server` is up and running.

# Step 4 (Nginx Files and Directories)

- After `installing package` of Nginx. The files of the `nginx` can be located in:

```bash
cd /etc/nginx
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2017.png)

- Here directory name `conf.d` is used to maintain the `virtual host` aka `v-shost` , so we can manage and `host` more then one website on a single machine.
- The main `configuration file of nginx` is `nginx.conf` . In the file we can do severla task e.g `set port number` ,

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2018.png)

 `view log file location` , 

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2019.png)

and many more information is available. It is `highly recommended` not to make any changes until it is very important. As a safety always make a backup before making changes inn the configuration file.

- To view the `error logs` in your `nginx` we have to go to the directory :

```bash
cd /var/log/nginix
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2020.png)

- The location to place our `website code` is :

```bash
	cd /var/www/html/
	
```

# Step 5 (Configuring The Virtual Host)

- We are doing to deploy a website name `petshop` on our `nginix` server. To do so, we have to make a file and configure the file as per our requirement. We will go into the directory:

```bash
cd /etc/nginx/conf.d
```

- In that directory we will create a file name `petshop.conf` :

```bash
touch petshop.conf
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2021.png)

> ***important : It is worth noting here that the file name we create should have an extension `.conf` . Apart from it it is consider as a good practice to have the website name as the file as well , so we can easily differentiate if we have two or more virtual host***
> 
- Now we have to do some editing in the file `petshop.conf` . Here it is worth mentioning that we must understand the syntax of the `nginx` when we put some code in the configuration file.
- The `editing in nginx` is consist of two part .
    1. Block : A block in the `configuration file`  start with a `variable or a name` e.g `server` or `http` etc. After the declaration of the name of the block , we make `curly brackets {}`. Inside the curly brackets . There can be multiple blocks inside one block. Inside the block we put the second part. For now a block look like this :
    
    ```bash
      server {
            listen       80;
            listen       [::]:80;
            server_name  _;
            root         /usr/share/nginx/html;
    
            # Load configuration files for the default server block.
            include /etc/nginx/default.d/*.conf;
    
            error_page 404 /404.html;
            location = /404.html {
            }
    
            error_page 500 502 503 504 /50x.html;
            location = /50x.html {
            }
        }
    
    ```
    
    - Directives : The arguments we passe inside a block is called blocks. The can be multiple
    
    ![The highlighted portion is called `directives` inside a `block`](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2022.png)
    
    The highlighted portion is called `directives` inside a `block`
    
- Now , coming back to our file name `petshop.conf` in the directory `cd /etc/nginx/conf.d`. Open the file in the `vim editior`

```bash
vim petshop.conf
```

We will configure the following settings:

```bash
server {
        listen 80 default_server;   #Define the port and also set it as a default
        server_name nginxproject.local  www.nginxproject.com; #Provide the name of the server to access the site
        index index.html index.php index.htm; #Defining the filename to access when try to connect
        root /var/www/petshop;  #Location where website code is places

}

```

Save the file and now `test nginx server` again using the command :

```bash
nginx -t
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2023.png)

Our nginx server is configured successfully.

- We also have to configure another file in :

```bash
vim /etc/hosts
```

The default setting in the file look like this :

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2024.png)

We need to add the `ip address` and also the `hostname url`

```bash
192.168.1.10 www.nginxproject.com
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2025.png)

# Step 6 (Downloading the Website Code):

- We have mentioned that a directory name `petshop` is present in the location `cd /var/www/` . So we have to create a directory in `cd /var/www

```bash
cd /var/www/

mkdir petshop
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2026.png)

- We have to download the code of the `website` from the url [`https://www.free-css.com/assets/files/free-css-templates/download/page284/pet-shop.zip](https://www.free-css.com/assets/files/free-css-templates/download/page284/pet-shop.zip) .`   We will run the command

```bash
wget https://www.free-css.com/assets/files/free-css-templates/download/page284/pet-shop.zip
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2027.png)

- Unzip the file and now we have `index,html` and remaining content on our directory which we mention in the `petshop.conf` file

# Part 7 (Checking port:80 is configured to NGINX):

- It is important to check that `port 80` is configured to `NGINX` because chances are previously you have configured it to `Apache web server`. In tha case, `nginx` will not work.
- So it is highly recommended to check and run the following command to check it :

```bash
lsof -i:80
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2028.png)

It clearly shows that `port 80` is configured to `nginx`

We can also check it using the `netstat` command:

```bash
netstat -pan | grep nginx
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2029.png)

# Part 8 (Firewall Configuration):

- We have to add the `services` in the `firewall` to allow the `http` and `https` communication. We run the command :

```bash
firewall-cmd --permanent --add-service=http --zone=public
firewall-cmd --permanent --add-service=https --zone=public
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2030.png)

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2031.png)

- Both services are added already. We can also check the list of all the services configured on our firewall

```bash
firewall-cmd --list-services

```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2032.png)

- After setting up the services on `firewall` it is good practice to restart it

```bash
systemctl restart firewalld
```

- Also restart the `nginx`

```bash
systemctl restart ngnix
```

- Check the configuration again using the command

```bash
nginx -t
```

If there is no error. Fire up the `web brwwer` and put test your website

# Step 9 (Testing Website)

- To test your website which you have hosted . Open the web browser and type in the ip address of your machine `192.168.1.10`

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2033.png)

- Also , use the `url` `www.nginxproject.com`

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2034.png)

# Hosting Another Website On same Server

# Step 10 (Creating Self signed SSL/TLS certificate):

- Now we will host another website on the same server.
- Since we are going to use the `local machine` to host website with `SSL/TLS certificate` . And we do not have own website for which we have bought `domain` . So , we have to use `self-signed certificate` for testing.
- First of all we will create a directory named `key_storage`  at `cd /root/key_storage`
- To generate a self key we will run the command:

```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/nginx/ssl/self-signed.key -out /etc/nginx/ssl/self-signed.crt

```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2035.png)

Few question will be asked answer them and the key will be generated.

- Now we have to move the `key` and `certificate` generated .Move the`self-signed.key` to the directory `/etc/pki/tls/private/` and `self-signed.cert` to `/etc/pki/tls/cert/` .

```bash
mv self-signed.key etc/pki/tls/private/

mv self-signed.crt /etc/pki/tls/cert/

```

# Step 11  (Making changes to the configuration file and creating new files)

- To enable `https` and `SLL/TLS` certification we need to first make some changes in the original `configuration` file of the `nginx` . Open the `nginx.conf` file

```bash
vi /etc/nginx/nginx.conf
```

- Scroll down and find the `# Settings for a TLS enabled server.` If the setting are `commented out` remove the `#` from that like in the screenshot below.

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2036.png)

- Our second website which we are going to host is a  `cars website` . We will create a new file name name `buycars.conf` in the directory of :
    
    ```bash
    cd /etc/nginx/conf.d/
    
    touch buycars.conf
    ```
    
- Open the file in `vi editor` to edit:

```bash
# HTTP server configuration for www.buycars.com and buycars.com
server {
    listen 80;
    listen [::]:80;
    server_name www.buycars.com buycars.com;

    # Redirect all HTTP requests to HTTPS
    return 301 https://$host$request_uri;
}

# HTTPS server configuration for www.buycars.com and buycars.com
server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    server_name www.buycars.com buycars.com;

    # Path to the self-signed SSL certificate and key
    ssl_certificate /etc/pki/tls/certs/self-signed.crt;
    ssl_certificate_key /etc/pki/tls/private/self-signed.key;

    # Additional SSL settings
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_prefer_server_ciphers on;
    ssl_ciphers 'ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384';

    root /var/www/buycars;
    index index.html index.php index.htm;
    location / {
        try_files $uri $uri/ =404;
    }

    # Error pages
    error_page 404 /404.html;
    location = /404.html {
        internal;
    }

    error_page 500 502 503 504 /50x.html;
    location = /50x.html {
        internal;
    }
}

```

- As we are now configuring our sites on `https` we also have to make changes to the configuration files of our `first website` which was [`www.nginxproject.com`](http://www.nginxproject.com)
- Open the file in vi editor `vi /etc/nginx/conf.d/petshop.conf` and make changes the file text will be:

```bash
# HTTP server configuration for nginxproject.local and www.nginxproject.com
server {
    listen 80;
    listen [::]:80;
    server_name nginxproject.local www.nginxproject.com;

    # Redirect all HTTP requests to HTTPS
    return 301 https://$host$request_uri;
}

# HTTPS server configuration for nginxproject.local and www.nginxproject.com
server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    server_name nginxproject.local www.nginxproject.com;

    # Path to the self-signed SSL certificate and key
    ssl_certificate /etc/pki/tls/certs/self-signed.crt;
    ssl_certificate_key /etc/pki/tls/private/self-signed.key;

    # Additional SSL settings
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_prefer_server_ciphers on;
    ssl_ciphers 'ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384';

root /var/www/petshop;
    index index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }
                                               
```

- Save the file and after that run the `nginx` test by running the command

```bash
nginx -t
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2037.png)

# Step 12 (Copying the website code to the directory)

- We have not created the directory to put our code in `cd /var/www/` . In our `configuration file` for  `buycars` we have mention the website location `cd /var/www/buycars` .
- So create a directory in `/var/www/` with the name of `buycars`

```bash
mkdir -p buycars
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2038.png)

- Open the directory `buy cars` and download the website code using command

```bash
wget https://www.free-css.com/assets/files/free-css-templates/download/page284/mical.zip
```

- Unzip the file and copy the entire files to `/var/www/buycars/` and delete other files which no longer needed.

# Step 13 (Adding the url into host file)

- Open the file in directory   `/etc/hosts` use the command :

```bash
vim /etc/hosts
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2039.png)

add `192.168.1.10 www.buycars.com`

Save the file

# Step 14 (Final Checking)

- Run the command to check the status of `nginx`

```bash
nginx -t
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2040.png)

- Reload the `nginx server`

```bash
systemctl reload nginx
```

- Check the list of `ports enable`

```bash
lsof -i :80

lsof -i:443
```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2041.png)

# Step 15 (Testing On web Browser)

- open the `firefox browser` on you Linux machine and type the address:

```bash
www.nginxproject.com

www.buycars.com
```

![Screenshot 2024-06-03 101010.png](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Screenshot_2024-06-03_101010.png)

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2042.png)

- Both websites are working fine

# Step 16 (Creating Individual LOG Directories for Individual Website)

- We know that by default the log files of the `nginx` is located in:

```bash
cd /var/log/nginx

```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2043.png)

- All the upstream websites information and error are placed in these logs. But it is a single file for all the websites. We can also create `individual log files` for `each website` and the use the `default log files` as a `consolidated` file for all the track record.
- To configure independent log we have to `change the configuration file` for each website we hosted in `/etc/nginx/conf.d` . First we will configure the `petshop website`

```bash
vi /etc/nginx/conf.d/petshop.conf

```

In the server block add the following line

```bash
    access_log /var/log/nginx/nginxproject.local.access.log;
    error_log /var/log/nginx/nginxproject.localnginxproject.log;

```

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2044.png)

- Restart the `nginx` using the command `nginx -t`
- And go to the directory `/var/log/nginx/`  you will see new log files will be created all the information for the website individually updated here

![Untitled](3%20Hosting%20Website%20on%20NGINX%20Server%20e4b71cb70eef405eaafca7456645b34a/Untitled%2045.png)

- Do the same for the other website if you wish to