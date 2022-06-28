```
events {
    worker_connections  1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;
    sendfile        on;
    keepalive_timeout  65;

    client_max_body_size     50m;
    client_body_buffer_size  10m; 
    client_header_timeout    1m;
    client_body_timeout      1m;
    
    gzip on;
    gzip_min_length  1k;
    gzip_buffers     4 16k;
    gzip_comp_level  4;
    gzip_types text/plain application/javascript application/x-javascript text/css application/xml text/javascript application/x-httpd-php image/jpeg image/gif image/png;
    gzip_vary on;

server {
        listen       80;
        server_name  123.56.96.86;
     
        location / {		
            root   html/blog;
            index  index.html index.htm; 
            try_files $uri $uri/ /index.html;	
        }
    		
    location ^~ /api/ {		
            proxy_pass http://123.56.96.86:8080/;
        proxy_set_header   Host             $host;
            proxy_set_header   X-Real-IP        $remote_addr;						
            proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
        }
    	
    }

server {
        listen       81;
        server_name  123.56.96.86;
     
        location / {		
            root   html/admin;
            index  index.html index.htm; 
            try_files $uri $uri/ /index.html;	
        }
    		
    location ^~ /api/ {		
            proxy_pass http://123.56.96.86:8080/;
        proxy_set_header   Host             $host;
            proxy_set_header   X-Real-IP        $remote_addr;						
            proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
        }
    	
    }

server {
        listen       82;
        server_name  123.56.96.86;
     
        location / {
          proxy_pass http://123.56.96.86:8080/websocket;
          proxy_http_version 1.1;
          proxy_set_header Upgrade $http_upgrade;
          proxy_set_header Connection "Upgrade";
          proxy_set_header Host $host:$server_port;
          proxy_set_header X-Real-IP $remote_addr;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
          proxy_set_header X-Forwarded-Proto $scheme;
       }
    
    }

server {
        listen       83;
        server_name  123.56.96.86;
     
        location / {		
          root C:/Users/Administrator/Desktop/nginx/html/upload/;
        }	
    }

 }
```