# install-nginx
    sudo apt update
    sudo apt install nginx


#  ufw app list    
    root@master:/home/sangbinlee9# sudo ufw app list
    Available applications:
      OpenSSH

# apt update      
    root@master:/home/sangbinlee9# sudo apt update
    sudo apt install nginx
  
    
# ufw app list    
    root@master:/home/sangbinlee9# sudo ufw app list
    Available applications:
      Nginx Full
      Nginx HTTP
      Nginx HTTPS
      OpenSSH
    root@master:/home/sangbinlee9#



    
    
    
# systemctl status nginx    
    root@master:/home/sangbinlee9# systemctl status nginx
    ● nginx.service - A high performance web server and a reverse proxy server
         Loaded: loaded (/lib/systemd/system/nginx.service; enabled; preset: enabled)
         Active: active (running) since Sun 2023-07-16 02:25:45 UTC; 54min ago
           Docs: man:nginx(8)
        Process: 8080 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
        Process: 8081 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
       Main PID: 8169 (nginx)
          Tasks: 5 (limit: 18892)
         Memory: 6.8M
            CPU: 36ms
         CGroup: /system.slice/nginx.service
                 ├─8169 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
                 ├─8171 "nginx: worker process"
                 ├─8172 "nginx: worker process"
                 ├─8173 "nginx: worker process"
                 └─8174 "nginx: worker process"
    
    Jul 16 02:25:45 master systemd[1]: Starting A high performance web server and a reverse proxy server...
    Jul 16 02:25:45 master systemd[1]: Started A high performance web server and a reverse proxy server.
    root@master:/home/sangbinlee9#


# ufw allow 'Nginx HTTP'
    root@master:/home/sangbinlee9# sudo ufw allow 'Nginx HTTP'
    Rule added
    Rule added (v6)
    root@master:/home/sangbinlee9# ufw status
    Status: active
    
    To                         Action      From
    --                         ------      ----
    6443/tcp                   ALLOW       Anywhere
    2379:2380/tcp              ALLOW       Anywhere
    10250/tcp                  ALLOW       Anywhere
    10251/tcp                  ALLOW       Anywhere
    10252/tcp                  ALLOW       Anywhere
    10259/tcp                  ALLOW       Anywhere
    10257/tcp                  ALLOW       Anywhere
    22/tcp                     ALLOW       Anywhere
    8080/tcp                   ALLOW       Anywhere
    80/tcp                     ALLOW       Anywhere
    Nginx HTTP                 ALLOW       Anywhere
    6443/tcp (v6)              ALLOW       Anywhere (v6)
    2379:2380/tcp (v6)         ALLOW       Anywhere (v6)
    10250/tcp (v6)             ALLOW       Anywhere (v6)
    10251/tcp (v6)             ALLOW       Anywhere (v6)
    10252/tcp (v6)             ALLOW       Anywhere (v6)
    10259/tcp (v6)             ALLOW       Anywhere (v6)
    10257/tcp (v6)             ALLOW       Anywhere (v6)
    22/tcp (v6)                ALLOW       Anywhere (v6)
    8080/tcp (v6)              ALLOW       Anywhere (v6)
    80/tcp (v6)                ALLOW       Anywhere (v6)
    Nginx HTTP (v6)            ALLOW       Anywhere (v6)
    
    root@master:/home/sangbinlee9#
  
  
# ufw allow 'Nginx HTTPS'
    root@master:/home/sangbinlee9# sudo ufw allow 'Nginx HTTPS'
    Rule added
    Rule added (v6)
    root@master:/home/sangbinlee9# ufw status
    Status: active
    
    To                         Action      From
    --                         ------      ----
    6443/tcp                   ALLOW       Anywhere
    2379:2380/tcp              ALLOW       Anywhere
    10250/tcp                  ALLOW       Anywhere
    10251/tcp                  ALLOW       Anywhere
    10252/tcp                  ALLOW       Anywhere
    10259/tcp                  ALLOW       Anywhere
    10257/tcp                  ALLOW       Anywhere
    22/tcp                     ALLOW       Anywhere
    8080/tcp                   ALLOW       Anywhere
    80/tcp                     ALLOW       Anywhere
    Nginx HTTP                 ALLOW       Anywhere
    Nginx HTTPS                ALLOW       Anywhere
    6443/tcp (v6)              ALLOW       Anywhere (v6)
    2379:2380/tcp (v6)         ALLOW       Anywhere (v6)
    10250/tcp (v6)             ALLOW       Anywhere (v6)
    10251/tcp (v6)             ALLOW       Anywhere (v6)
    10252/tcp (v6)             ALLOW       Anywhere (v6)
    10259/tcp (v6)             ALLOW       Anywhere (v6)
    10257/tcp (v6)             ALLOW       Anywhere (v6)
    22/tcp (v6)                ALLOW       Anywhere (v6)
    8080/tcp (v6)              ALLOW       Anywhere (v6)
    80/tcp (v6)                ALLOW       Anywhere (v6)
    Nginx HTTP (v6)            ALLOW       Anywhere (v6)
    Nginx HTTPS (v6)           ALLOW       Anywhere (v6)
    
    root@master:/home/sangbinlee9#
    

# 시작
sudo systemctl start nginx

# 종료
sudo systemctl stop nginx

# 재시작
sudo systemctl restart nginx

# 리로드 (변경된 설정을 적용하는 경우 사용. 기존 연결을 끊지 않음.)
sudo systemctl reload nginx

# 기본적으로 서버 시작 시 nginx가 자동으로 실행되는데, 이를 막고 싶은 경우
sudo systemctl disable nginx

# 서버 시작 시 자동으로 nginx를 실행하고 싶은 경우
sudo systemctl enable nginx





# HTTPS 적용
## sudo apt install certbot python3-certbot-nginx

    root@master:/home/sangbinlee9# sudo ufw allow 'Nginx Full' # HTTP와 HTTPS 모두 허용
    sudo ufw delete allow 'Nginx HTTP' # 기존의 HTTP 허용 설정 제거
    Rule added
    Rule added (v6)
    Rule deleted
    Rule deleted (v6)
    root@master:/home/sangbinlee9# sudo ufw delete allow 'Nginx HTTPS' # 기존의 HTTP 허용 설정 제거
    Rule deleted
    Rule deleted (v6)
    root@master:/home/sangbinlee9# ufw status
    Status: active
    
    To                         Action      From
    --                         ------      ----
    6443/tcp                   ALLOW       Anywhere
    2379:2380/tcp              ALLOW       Anywhere
    10250/tcp                  ALLOW       Anywhere
    10251/tcp                  ALLOW       Anywhere
    10252/tcp                  ALLOW       Anywhere
    10259/tcp                  ALLOW       Anywhere
    10257/tcp                  ALLOW       Anywhere
    22/tcp                     ALLOW       Anywhere
    8080/tcp                   ALLOW       Anywhere
    80/tcp                     ALLOW       Anywhere
    Nginx Full                 ALLOW       Anywhere
    6443/tcp (v6)              ALLOW       Anywhere (v6)
    2379:2380/tcp (v6)         ALLOW       Anywhere (v6)
    10250/tcp (v6)             ALLOW       Anywhere (v6)
    10251/tcp (v6)             ALLOW       Anywhere (v6)
    10252/tcp (v6)             ALLOW       Anywhere (v6)
    10259/tcp (v6)             ALLOW       Anywhere (v6)
    10257/tcp (v6)             ALLOW       Anywhere (v6)
    22/tcp (v6)                ALLOW       Anywhere (v6)
    8080/tcp (v6)              ALLOW       Anywhere (v6)
    80/tcp (v6)                ALLOW       Anywhere (v6)
    Nginx Full (v6)            ALLOW       Anywhere (v6)
    
    root@master:/home/sangbinlee9#


# sudo certbot --nginx -d 도메인 이름 -d www.도메인 이름 
    
    root@master:/home/sangbinlee9# sudo certbot --nginx -d jy6.shop -d www.jy6.shop
    Saving debug log to /var/log/letsencrypt/letsencrypt.log
    Enter email address (used for urgent renewal and security notices)
     (Enter 'c' to cancel):  sangbinlee9@gmail.com
    
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    Please read the Terms of Service at
    https://letsencrypt.org/documents/LE-SA-v1.3-September-21-2022.pdf. You must
    agree in order to register with the ACME server. Do you agree?
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    (Y)es/(N)o: Y
    
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    Would you be willing, once your first certificate is successfully issued, to
    share your email address with the Electronic Frontier Foundation, a founding
    partner of the Let's Encrypt project and the non-profit organization that
    develops Certbot? We'd like to send you email about our work encrypting the web,
    EFF news, campaigns, and ways to support digital freedom.
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    (Y)es/(N)o: Y
    Account registered.
    Requesting a certificate for jy6.shop and www.jy6.shop
    
    Successfully received certificate.
    Certificate is saved at: /etc/letsencrypt/live/jy6.shop/fullchain.pem
    Key is saved at:         /etc/letsencrypt/live/jy6.shop/privkey.pem
    This certificate expires on 2023-10-14.
    These files will be updated when the certificate renews.
    Certbot has set up a scheduled task to automatically renew this certificate in the background.
    
    Deploying certificate
    Successfully deployed certificate for jy6.shop to /etc/nginx/sites-enabled/default
    Successfully deployed certificate for www.jy6.shop to /etc/nginx/sites-enabled/default
    Congratulations! You have successfully enabled HTTPS on https://jy6.shop and https://www.jy6.shop
    
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    If you like Certbot, please consider supporting our work by:
     * Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
     * Donating to EFF:                    https://eff.org/donate-le
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    root@master:/home/sangbinlee9#


# systemctl status certbot.timer
    root@master:/home/sangbinlee9# sudo systemctl status certbot.timer
    ● certbot.timer - Run certbot twice daily
         Loaded: loaded (/lib/systemd/system/certbot.timer; enabled; preset: enabled)
         Active: active (waiting) since Sun 2023-07-16 03:28:25 UTC; 8min ago
          Until: Sun 2023-07-16 03:28:25 UTC; 8min ago
        Trigger: Sun 2023-07-16 22:16:28 UTC; 18h left
       Triggers: ● certbot.service
    
    Jul 16 03:28:25 master systemd[1]: Started Run certbot twice daily.
    root@master:/home/sangbinlee9#

# date
    root@master:/home/sangbinlee9# date
    Sun Jul 16 03:38:24 AM UTC 2023


# sudo certbot renew --dry-run

    
    root@master:/home/sangbinlee9# sudo certbot renew --dry-run
    Saving debug log to /var/log/letsencrypt/letsencrypt.log
    
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    Processing /etc/letsencrypt/renewal/jy6.shop.conf
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    Account registered.
    Simulating renewal of an existing certificate for jy6.shop and www.jy6.shop
    
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    Congratulations, all simulated renewals succeeded:
      /etc/letsencrypt/live/jy6.shop/fullchain.pem (success)
    - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
    root@master:/home/sangbinlee9#





![image](https://github.com/sangbinlee/install-nginx/assets/4024414/769127de-51dd-44cc-ba6e-808a23c28ff1)







![image](https://github.com/sangbinlee/install-nginx/assets/4024414/f7eae624-cd34-4b32-81d4-85bdd1cf5b42)

![image](https://github.com/sangbinlee/install-nginx/assets/4024414/00943c2d-ddc9-4029-81e1-7ef26b6b8928)


![image](https://github.com/sangbinlee/install-nginx/assets/4024414/7fbd8229-e38f-47da-9373-7984ea282421)


![image](https://github.com/sangbinlee/install-nginx/assets/4024414/1bc26f98-5a64-4625-80c7-870462c4b1f0)




![image](https://github.com/sangbinlee/install-nginx/assets/4024414/4fad14f8-616c-4485-9b83-3520f47de2a3)



![image](https://github.com/sangbinlee/install-nginx/assets/4024414/e80aefaf-4fc6-491a-bcfa-e7e384e438bd)


![image](https://github.com/sangbinlee/install-nginx/assets/4024414/7f6aa286-eba3-4229-b809-c15b9a1d0b63)3




# Configuring Nginx as a reverse proxy


    
    root@master:/home/sangbinlee9# systemctl --full status nginx
    ● nginx.service - A high performance web server and a reverse proxy server
         Loaded: loaded (/lib/systemd/system/nginx.service; enabled; preset: enabled)
         Active: active (running) since Sun 2023-07-16 02:25:45 UTC; 1h 30min ago
           Docs: man:nginx(8)
       Main PID: 8169 (nginx)
          Tasks: 5 (limit: 18892)
         Memory: 8.9M
            CPU: 595ms
         CGroup: /system.slice/nginx.service
                 ├─ 8169 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
                 ├─12557 "nginx: worker process"
                 ├─12558 "nginx: worker process"
                 ├─12559 "nginx: worker process"
                 └─12560 "nginx: worker process"
    
    Jul 16 02:25:45 master systemd[1]: Starting A high performance web server and a reverse proxy server...
    Jul 16 02:25:45 master systemd[1]: Started A high performance web server and a reverse proxy server.
    root@master:/home/sangbinlee9#


#  nginx -t
    root@master:/home/sangbinlee9# nginx -t
    nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
    nginx: configuration file /etc/nginx/nginx.conf test is successful




![image](https://github.com/sangbinlee/install-nginx/assets/4024414/9cbc6347-5f80-4ed9-b7ea-fb82ad1d6ea0)







![image](https://github.com/sangbinlee/install-nginx/assets/4024414/b017c5d7-d451-4655-900a-c810c45ee276)



![image](https://github.com/sangbinlee/install-nginx/assets/4024414/daa78979-dd80-42cc-a925-cbd4610f7845)




![image](https://github.com/sangbinlee/install-nginx/assets/4024414/1a919a69-2972-4979-9900-35589315e876)



# hostnamectl status
    root@master:/etc/nginx/conf.d# hostnamectl status
     Static hostname: master
           Icon name: computer
          Machine ID: f13d61e1b9eb4977bb8fdadeacdd00a9
             Boot ID: aecda94365284301ab831660064e81d1
    Operating System: Ubuntu 22.10
              Kernel: Linux 5.19.0-46-generic
        Architecture: x86-64
     Hardware Vendor: Hewlett-Packard
      Hardware Model: HP EliteBook 840 G2
    Firmware Version: M71 Ver. 01.31
    root@master:/etc/nginx/conf.d#




# Reverse proxy - Nginx 
    In situations where you have existing web sites on your server, you may find it useful to run Jenkins (or the servlet container that Jenkins runs in) behind Nginx, so that you can bind Jenkins to the part of a bigger website that you may have. This section discusses some of the approaches for doing this.
    
    When a request arrives for certain URLs, Nginx becomes a proxy and further forward that request to Jenkins, then it forwards the response back to the client. A typical set up for mod_proxy would look like this:
    
    upstream jenkins {
      keepalive 32; # keepalive connections
      server 127.0.0.1:8080; # jenkins ip and port
    }
    
    # Required for Jenkins websocket agents
    map $http_upgrade $connection_upgrade {
      default upgrade;
      '' close;
    }
    
    server {
      listen          80;       # Listen on port 80 for IPv4 requests
    
      server_name     jenkins.example.com;  # replace 'jenkins.example.com' with your server domain name
    
      # this is the jenkins web root directory
      # (mentioned in the output of "systemctl cat jenkins")
      root            /var/run/jenkins/war/;
    
      access_log      /var/log/nginx/jenkins.access.log;
      error_log       /var/log/nginx/jenkins.error.log;
    
      # pass through headers from Jenkins that Nginx considers invalid
      ignore_invalid_headers off;
    
      location ~ "^/static/[0-9a-fA-F]{8}\/(.*)$" {
        # rewrite all static files into requests to the root
        # E.g /static/12345678/css/something.css will become /css/something.css
        rewrite "^/static/[0-9a-fA-F]{8}\/(.*)" /$1 last;
      }
    
      location /userContent {
        # have nginx handle all the static requests to userContent folder
        # note : This is the $JENKINS_HOME dir
        root /var/lib/jenkins/;
        if (!-f $request_filename){
          # this file does not exist, might be a directory or a /**view** url
          rewrite (.*) /$1 last;
          break;
        }
        sendfile on;
      }
    
      location / {
          sendfile off;
          proxy_pass         http://jenkins;
          proxy_redirect     default;
          proxy_http_version 1.1;
    
          # Required for Jenkins websocket agents
          proxy_set_header   Connection        $connection_upgrade;
          proxy_set_header   Upgrade           $http_upgrade;
    
          proxy_set_header   Host              $host;
          proxy_set_header   X-Real-IP         $remote_addr;
          proxy_set_header   X-Forwarded-For   $proxy_add_x_forwarded_for;
          proxy_set_header   X-Forwarded-Proto $scheme;
          proxy_max_temp_file_size 0;
    
          #this is the maximum upload size
          client_max_body_size       10m;
          client_body_buffer_size    128k;
    
          proxy_connect_timeout      90;
          proxy_send_timeout         90;
          proxy_read_timeout         90;
          proxy_buffering            off;
          proxy_request_buffering    off; # Required for HTTP CLI commands
          proxy_set_header Connection ""; # Clear for keepalive
      }
    
    }
    

![image](https://github.com/sangbinlee/install-nginx/assets/4024414/a452a47f-417c-40d3-8af4-8a5d76f2c087)

![image](https://github.com/sangbinlee/install-nginx/assets/4024414/9024e70f-e565-40ef-95cd-4564fbaf382e)

![image](https://github.com/sangbinlee/install-nginx/assets/4024414/9e669eb0-7c66-466f-a122-1cf2ef46abfc)

![image](https://github.com/sangbinlee/install-nginx/assets/4024414/53274b97-349d-4a55-87d8-6983a7dd5ecc)

![image](https://github.com/sangbinlee/install-nginx/assets/4024414/e62e00e2-ffd1-4502-af3f-4a701c5d0178)


![image](https://github.com/sangbinlee/install-nginx/assets/4024414/9662493b-1da8-49c0-bf3b-d4fc792f3d7c)


![image](https://github.com/sangbinlee/install-nginx/assets/4024414/2c891a7e-be78-4f73-a2d1-df551b923dcd)





