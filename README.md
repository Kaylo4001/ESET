# ESET
suod docker compose up -d
config nginx.cong ---> /etc/nginx/conf.d/vi eset.conf
server {
    listen                  80;
    return                  301 https://$host$request_uri;
    server_name             eset-console.srv.bigbang.dotin.ir;
}

server {
    listen                  443 ssl;
    server_name             eset-console.srv.bigbang.dotin.ir;
    ssl_certificate         /etc/ssl/certs/srv.bigbang.dotin.ir/cert.pem;
    ssl_certificate_key     /etc/ssl/private/srv.bigbang.dotin.ir/key.pem;
    ssl_password_file       /etc/ssl/private/srv.bigbang.dotin.ir/pass.txt;
    location / {
        proxy_pass          http://localhost:8080;
    }
}

nginx -s reload
systemctl restart nginx.services
systemctl restart nginx
