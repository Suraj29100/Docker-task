Task2

Deploy a web service using Docker, Docker Compose, and systemd.

 Tasks Implemented:


 
1️⃣ Dockerfile

Custom NGINX image with modified index.html

FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html


2️⃣ docker-compose.yml

Restart policy enabled

Port mapping: 8080 → 80

Named container

restart: always
ports:
  - "8080:80"

3️⃣ systemd Service

Manages Docker Compose as a system service.

[Service]
ExecStart=/usr/bin/docker-compose up -d
ExecStop=/usr/bin/docker-compose down
Restart=always

4️⃣ Log Handling

Docker logs available via:

docker logs nginx_onprem

5️⃣ Application Access
curl http://localhost:8080


Output:

<h1>NGINX running via Docker Compose & systemd</h1>


Accessible from browser using:

http://<EC2-PUBLIC-IP>:8080
