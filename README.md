# Bitwise Learn - Docker Apache HTTPD

This project uses Docker only. Docker Compose is NOT required.

## Files

- index.html
- style.css
- website.pdf
- Dockerfile
- .dockerignore
- README.md

## 1. Extract the project

```bash
unzip bitwise-httpd-docker.zip
cd bitwise-httpd-docker
```

## 2. Build Docker image

```bash
docker build -t bitwise-httpd .
```

## 3. Run container on port 80

```bash
docker run -d --name bitwise-httpd -p 80:80 --restart unless-stopped bitwise-httpd
```

## 4. Check container

```bash
docker ps
```

## 5. Check logs

```bash
docker logs bitwise-httpd
```

## 6. Test from server

```bash
curl http://localhost
```

## 7. Open from your computer

```text
http://YOUR_SERVER_IP
```

## If port 80 is already in use

Check:

```bash
sudo ss -tulpn | grep :80
```

If Ubuntu Apache is using port 80:

```bash
sudo systemctl stop apache2
sudo systemctl disable apache2
```

Then run:

```bash
docker run -d --name bitwise-httpd -p 80:80 --restart unless-stopped bitwise-httpd
```

## Firewall

```bash
sudo ufw allow 80/tcp
sudo ufw status
```

## After changing index.html

Remove the old container:

```bash
docker rm -f bitwise-httpd
```

Rebuild:

```bash
docker build -t bitwise-httpd .
```

Run again:

```bash
docker run -d --name bitwise-httpd -p 80:80 --restart unless-stopped bitwise-httpd
```

## Stop

```bash
docker stop bitwise-httpd
```

## Start

```bash
docker start bitwise-httpd
```

## Remove

```bash
docker rm -f bitwise-httpd
```

## Important

There is NO docker-compose.yml in this project.
Only Dockerfile and standard Docker commands are required.
# bitwise-httpd-docker
