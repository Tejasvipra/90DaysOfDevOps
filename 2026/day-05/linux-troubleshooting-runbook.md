Runbook: Port Conflict (Two services cannot run on same port)
Purpose

Resolve issues when two services try to use the same port (example: Apache and Nginx on port 80).

When to Use
Service fails to start
Error shows “Address already in use”
Web service not accessible

1. Check service status:
ubuntu:~$ lsb_release -a

        No LSB modules are available.
        Distributor ID: Ubuntu
        Description:    Ubuntu 24.04.3 LTS
        Release:        24.04
        Codename:       noble

systemctl status apache2
systemctl status nginx

       × apache2.service - The Apache HTTP Server
         Loaded: loaded (/usr/lib/systemd/system/apache2.service; enabled; preset: enabled)
         Active: failed (Result: exit-code) since Mon 2026-02-02 14:29:06 UTC; 37s ago
           Docs: https://httpd.apache.org/docs/2.4/
        Process: 4282 ExecStart=/usr/sbin/apachectl start (code=exited, status=1/FAILURE)
            CPU: 31ms
    
        Feb 02 14:29:06 ubuntu systemd[1]: Starting apache2.service - The Apache HTTP Server...
        Feb 02 14:29:06 ubuntu apachectl[4284]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1. Set the 'ServerName' directive glob>
        Feb 02 14:29:06 ubuntu apachectl[4284]: (98)Address already in use: AH00072: make_sock: could not bind to address [::]:80
        Feb 02 14:29:06 ubuntu apachectl[4284]: (98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:80
        Feb 02 14:29:06 ubuntu apachectl[4284]: no listening sockets available, shutting down
        Feb 02 14:29:06 ubuntu apachectl[4284]: AH00015: Unable to open logs
        Feb 02 14:29:06 ubuntu systemd[1]: apache2.service: Control process exited, code=exited, status=1/FAILURE
        Feb 02 14:29:06 ubuntu systemd[1]: apache2.service: Failed with result 'exit-code'.
        Feb 02 14:29:06 ubuntu systemd[1]: Failed to start apache2.service - The Apache HTTP Server.

journalctl -xeu apache2.service


ubuntu:~$ sudo lsof -i :80

        COMMAND  PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
        nginx   2436     root    5u  IPv4  15954      0t0  TCP *:http (LISTEN)
        nginx   2436     root    6u  IPv6  15955      0t0  TCP *:http (LISTEN)
        nginx   2439 www-data    5u  IPv4  15954      0t0  TCP *:http (LISTEN)
        nginx   2439 www-data    6u  IPv6  15955      0t0  TCP *:http (LISTEN)
        ubuntu:~$ cd /etc/nginx/sites-available/       
ubuntu:/etc/nginx/sites-available$ ls
default

2.Fix Option 2: Change port of one service

 ubuntu:/etc/nginx/sites-available$ ls
  default
  
  ubuntu:/etc/nginx/sites-available$ vim default 
  
   ubuntu:/etc/nginx/sites-available$ sudo nginx -t
          
           nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
            nginx: configuration file /etc/nginx/nginx.conf test is successful
            ubuntu:/etc/nginx/sites-available$ systemctl restart nginx
            ubuntu:/etc/nginx/sites-available$ systemctl start apache2
            ubuntu:/etc/nginx/sites-available$ systemctl status apache2
            ● apache2.service - The Apache HTTP Server
                 Loaded: loaded (/usr/lib/systemd/system/apache2.service; enabled; preset: enabled)
                 Active: active (running) since Mon 2026-02-02 14:32:55 UTC; 4s ago
                   Docs: https://httpd.apache.org/docs/2.4/
                Process: 4500 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCCESS)
               Main PID: 4503 (apache2)
                  Tasks: 55 (limit: 2237)
                 Memory: 5.1M (peak: 5.2M)
                    CPU: 45ms
                 CGroup: /system.slice/apache2.service
                         ├─4503 /usr/sbin/apache2 -k start
                         ├─4505 /usr/sbin/apache2 -k start
                         └─4506 /usr/sbin/apache2 -k start
      
      Feb 02 14:32:55 ubuntu systemd[1]: Starting apache2.service - The Apache HTTP Server...
      Feb 02 14:32:55 ubuntu apachectl[4502]: AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1. Set the 'ServerName' directive glob>
      Feb 02 14:32:55 ubuntu systemd[1]: Started apache2.service - The Apache HTTP Server.
      lines 1-17/17 (END)





ubuntu:~$ lsof -i :80

    COMMAND  PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
    apache2 2355     root    4u  IPv6  13685      0t0  TCP *:http (LISTEN)
    apache2 2357 www-data    4u  IPv6  13685      0t0  TCP *:http (LISTEN)
    apache2 2359 www-data    4u  IPv6  13685      0t0  TCP *:http (LISTEN)

ubuntu:~$ ps -p 2359

    PID TTY          TIME CMD
    2359 ?        00:00:00 apache2

ubuntu:~$ smem -p 2355
 
      PID User     Command                         Swap      USS      PSS      RSS 
      723 root     /sbin/agetty -o -p -- \u --    0.00%    0.01%    0.01%    0.10% 
      690 root     /sbin/agetty -o -p -- \u --    0.00%    0.01%    0.01%    0.11% 
      786 dhcpcd   dhcpcd: [control proxy] enp    0.00%    0.01%    0.02%    0.10% 
     2465 www-data /usr/bin/htcacheclean -d 12    0.00%    0.01%    0.02%    0.09% 
      785 dhcpcd   dhcpcd: [network proxy] enp    0.00%    0.01%    0.02%    0.10% 
     1123 dhcpcd   dhcpcd: [DHCP6 proxy] fe80:    0.00%    0.01%    0.02%    0.11% 
      877 dhcpcd   dhcpcd: [BPF ARP] enp1s0 17    0.00%    0.01%    0.02%    0.11% 
     1135 dhcpcd   dhcpcd: [BOOTP proxy] 172.3    0.00%    0.01%    0.02%    0.12% 


ubuntu:~$ mkdir /tmp/example-runbook 

ubuntu:/etc/apache2$ cp /etc/apache2/apache2.conf /tmp/example-runbook/  && cat /etc/apache2/apache2.conf 
