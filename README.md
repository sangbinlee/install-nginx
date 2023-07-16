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
    
