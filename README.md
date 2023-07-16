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
