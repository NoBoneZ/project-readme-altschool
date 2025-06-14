# AltSchool Landing Page Deployment

This repository contains the source code and complete instructions for deploying the AltSchool landing page to a production-ready server using AWS EC2 and Nginx.

---

## 🖥️ Server Setup

- **Cloud Provider**: Amazon Web Services (AWS)
- **Instance Type**: EC2 (Ubuntu 20.04)
- **Purpose**: Hosting a static landing page

### Steps:
1. **Launched EC2 Instance** with Ubuntu 22.04.
2. **Configured Security Group** to allow:
   - HTTP (Port 80)
   - HTTPS (Port 443)
   - SSH (Port 22)

3. **Connected to the server** via SSH:
   ```bash
   ssh -i {{my-key}}.pem ubuntu@your-ec2-ip
````

4. **Updated packages**:

   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

---

## Web Server Setup

* **Web Server**: Nginx

### Installation:

```bash
sudo apt install nginx -y
```

### Start and enable Nginx:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

##  Deployment

1. **Uploaded landing page files** to the server directory:

   ```
   /home/ubuntu/altschool/altschool-project-landing-page/
   ```

2. **Created Nginx configuration file**:

   ```bash
   sudo nano /etc/nginx/sites-available/altschool
   ```

3. **Added the following config**:

   ```nginx
   server {
       listen 80;
       server_name {{server_ip}};

       root /home/ubuntu/altschool/altschool-project-landing-page;
       index index.html;

       location / {
           try_files $uri $uri/ =404;
       }
   }
   ```

4. **Enabled the configuration**:

   ```bash
   sudo ln -s /etc/nginx/sites-available/altschool /etc/nginx/sites-enabled/
   ```

5. **Tested Nginx config**:

   ```bash
   sudo nginx -t
   ```

6. **Restarted Nginx**:

   ```bash
   sudo systemctl restart nginx
   ```

---

## ✅ Result

You can now visit the landing page in your browser using:

```
http://13.60.246.21/
```


## 🙋‍♂️ Author

Abraham Adekunle
[GitHub](https://github.com/abrahamadekunle)

```
