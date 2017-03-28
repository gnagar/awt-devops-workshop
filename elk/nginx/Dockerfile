FROM localhost:5000/nginx
COPY kibana.htpasswd /etc/nginx/conf.d/kibana.htpasswd
COPY nginx.conf /etc/nginx/nginx.conf
COPY kibana.conf /etc/nginx/sites-enabled/kibana.conf