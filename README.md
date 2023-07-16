# install-nginx
    sudo apt update
    sudo apt install nginx


    
    root@master:/home/sangbinlee9# sudo ufw app list
    Available applications:
      OpenSSH
    root@master:/home/sangbinlee9# sudo apt update
    sudo apt install nginx
  
    
    
    root@master:/home/sangbinlee9# sudo ufw app list
    Available applications:
      Nginx Full
      Nginx HTTP
      Nginx HTTPS
      OpenSSH
    root@master:/home/sangbinlee9#



    
    
    
    
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
  
  
    
