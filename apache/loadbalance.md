# Load balance

Montando um Load balancer usando apache mod_proxy e mod_proxy_balancer

    NameVirtualHost *:80

Header add Set-Cookie "ROUTEID=.%{BALANCER_WORKER_ROUTE}e; path=/" env=BALANCER_ROUTE_CHANGED

    <Proxy balancer://teste>
    BalancerMember http://127.0.0.1:80 route=1 connectiontimeout=20ms retry=60 loadfactor=3
    BalancerMember http://srv-1.netforcews.com:80 route=2 connectiontimeout=20ms retry=60 loadfactor=2
    BalancerMember http://54.207.255.219:80 route=3 connectiontimeout=20ms retry=60 loadfactor=2

ProxySet stickysession=ROUTEID lbmethod=byrequests

    ProxySet stickysession=ROUTEID lbmethod=bytraffic

ProxySet stickysession=ROUTEID lbmethod=bybusyness

    </Proxy>

    <VirtualHost *:80>
    ServerName lb.netforcews.com
    ServerAlias lb.netforcews.com
  
  DocumentRoot /var/www/html
  
    ProxyPass         / balancer://teste
    ProxyPassReverse  / balancer://teste
  
    <Directory />
    AllowOverride All
    </Directory>
    </VirtualHost>

    <VirtualHost *:80>
    ServerName 127.0.0.1
  
ServerAlias www.netforcews.com

    DocumentRoot /var/www/html

    <Directory />
    AllowOverride All
    </Directory>
    </VirtualHost>
