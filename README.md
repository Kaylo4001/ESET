# ESET
suod docker compose up -d

config nginx.cong ---> /etc/nginx/conf.d/vi eset.conf
server {
    listen                  80;
    return                  301 https://$host$request_uri;
    server_name             "server name url";
}

server {
    listen                  443 ssl;
    server_name             "server name url";
    ssl_certificate         /etc/ssl/certs/server name/cert.pem;
    ssl_certificate_key     /etc/ssl/private/server name/key.pem;
    ssl_password_file       /etc/ssl/private/sarver name/pass.txt;
    location / {
        proxy_pass          http://localhost:8080;
    }
}



nginx -s reload

systemctl restart nginx.services

systemctl restart nginx
