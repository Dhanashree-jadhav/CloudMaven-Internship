# task 1 : Test all NGINX management commands
Install NGINX and confirm the welcome page loads at http://localhost.
Run each management command (start, stop, restart, reload, enable) and note what happens
to the service each time.
Intentionally add a syntax error to nginx.conf (e.g., missing semicolon) and confirm nginx -t
catches it before any reload.
```bash
# Introduce a syntax error
sudo nano /etc/nginx/nginx.conf # remove a semicolon
sudo nginx -t # should report: [emerg] ...
# Fix and retest
sudo nginx -t # should report: syntax is ok
```
<img width="1897" height="692" alt="web_1 1" src="https://github.com/user-attachments/assets/dc5b2beb-fac2-45e1-9637-8c475f32564f" />
<img width="1757" height="442" alt="web_1 2" src="https://github.com/user-attachments/assets/865a058b-4531-475f-b3ce-882d2a76d59a" />
<img width="1870" height="423" alt="web_1 3" src="https://github.com/user-attachments/assets/fb2db87d-5fb9-420b-988f-dc69fb86d41f" />
<img width="1918" height="768" alt="web_1 4" src="https://github.com/user-attachments/assets/fc8fed17-4f53-4512-8680-6f067b4045f1" />
<img width="1911" height="708" alt="web_t_2 1" src="https://github.com/user-attachments/assets/79b07b69-828b-43f0-9304-c2dd7e4c0c0e" />
<img width="1920" height="1080" alt="web_t_2 2" src="https://github.com/user-attachments/assets/dce4cd6a-2f7e-4701-9481-f30f45cd0c2c" />

# task 2 : Explore the NGINX config hierarchy
Open /etc/nginx/nginx.conf and identify the main, events, and http contexts.
Note the worker_processes and worker_connections values and research what changing them
would do.
List all files currently in sites-available and sites-enabled and verify which symlinks exist
```bash
cat /etc/nginx/nginx.conf
# List enabled sites and verify symlinks
ls -la /etc/nginx/sites-enabled/
# Check current worker settings
grep -E 'worker_processes|worker_connections' /etc/nginx/nginx.conf
```
<img width="1916" height="123" alt="web_2 1" src="https://github.com/user-attachments/assets/102976d9-e12b-4ec8-b676-61d592c4cc99" />
<img width="1920" height="1080" alt="web_2 2" src="https://github.com/user-attachments/assets/ca4b5970-0e03-4d69-bdb1-500047fc81a5" />
<img width="1920" height="1080" alt="web_2 3" src="https://github.com/user-attachments/assets/9a4e8f65-9ae6-4e86-af29-4f2fe1cfc06b" />
<img width="1906" height="127" alt="web_2 4" src="https://github.com/user-attachments/assets/a765f234-0076-41d6-84cd-0c981e89f9a8" />

# task 3 :  Host a multi-page static site
Create a site under /var/www/mysite.local with at least 3 pages: index.html, about.html,
contact.html.
Write a proper server block config and enable it.
Add mysite.local to /etc/hosts and verify all 3 pages load via http://mysite.local/about.html etc.
Test what happens when you visit a non-existent page — confirm NGINX returns a 404.
```bash
sudo mkdir -p /var/www/mysite.local/html
echo '<h1>Home</h1>' > /var/www/mysite.local/html/index.html
echo '<h1>About</h1>' > /var/www/mysite.local/html/about.html
echo '<h1>Contact</h1>' > /var/www/mysite.local/html/contact.html
# Test all pages
curl http://mysite.local
curl http://mysite.local/about.html
curl -o /dev/null -s -w '%{http_code}' http://mysite.local/missing
# Expected: 404
```
<img width="1901" height="276" alt="web_3 1" src="https://github.com/user-attachments/assets/ba3e3219-d59a-45f5-9752-4124df039a89" />
<img width="1920" height="1080" alt="web_3 2" src="https://github.com/user-attachments/assets/3c180fa8-2f4b-44c0-a101-738a170be9d7" />
<img width="1896" height="161" alt="web_3 3" src="https://github.com/user-attachments/assets/54f36854-d05d-4254-89e3-74e21fb1744c" />
<img width="1920" height="1080" alt="web_3 4" src="https://github.com/user-attachments/assets/b403348b-81d3-4668-bb30-daeb7d5b0731" />
<img width="1255" height="182" alt="web_3 5" src="https://github.com/user-attachments/assets/05c6e639-b2be-4554-8277-bc57774a68e3" />

# task 4 : Run two Docker containers and proxy each on a Reverse Proxy & Docker
Run two Docker containers: nginx:alpine on port 8081 and traefik/whoami on port 8082.
Configure Nginx with two location blocks: /app1 proxying to :8081 and /app2 proxying to :8082.
Verify both paths return distinct responses at http://myapp.local/app1 and
http://myapp.local/app2.
Confirm the X-Real-IP header is set correctly using the whoami endpoint.
```bash
docker run -d --name app1 -p 8081:80 nginx:alpine
docker run -d --name app2 -p 8082:80 traefik/whoami
# Nginx location blocks to add:
# location /app1/ { proxy_pass http://127.0.0.1:8081/; }
# location /app2/ { proxy_pass http://127.0.0.1:8082/; }
curl http://myapp.local/app1/
curl http://myapp.local/app2/
```

<img width="1920" height="1080" alt="web_4 1" src="https://github.com/user-attachments/assets/118ba03e-4d19-44b1-af9e-a481309eaf8d" />
<img width="1666" height="580" alt="web_4 2" src="https://github.com/user-attachments/assets/c0a26273-e9e3-4539-bc40-c3dd9e1bfafe" />
<img width="1920" height="1080" alt="web_4 3" src="https://github.com/user-attachments/assets/b3894e0b-3119-42c6-8438-b932fcc46b81" />
<img width="1918" height="960" alt="web_4 4" src="https://github.com/user-attachments/assets/ba7c7b5d-6447-4b58-a19e-bfd36ee35f12" />

# task 5 : Host app1.local and app2.local with unique content and verify isolation
Complete the full practical session: create directories, configs, and /etc/hosts entries for
app1.local and app2.local.
Add a unique HTML page to each site so you can visually confirm you are hitting the right
backend.
Disable app2.local (remove its symlink) and confirm http://app2.local returns a 404 or
connection error while app1.local still works.
Re-enable app2.local and reload NGINX.
```bash
# Disable app2.local
sudo rm /etc/nginx/sites-enabled/app2.local
sudo nginx -t && sudo systemctl reload nginx
# Confirm app1 still works, app2 does not
curl http://app1.local # Expected: 200
curl http://app2.local # Expected: connection refused or 404
# Re-enable
sudo ln -s /etc/nginx/sites-available/app2.local /etc/nginx/sites-enabled/
sudo systemctl reload nginx
```
<img width="1920" height="1080" alt="web_5 1" src="https://github.com/user-attachments/assets/6bac44bd-c530-4ebc-a85c-e85b1cc00a9e" />
<img width="1920" height="1080" alt="web_5 2" src="https://github.com/user-attachments/assets/e9e9830d-8dfb-449b-a915-1535ccdefe58" />
<img width="1857" height="281" alt="web_5 3" src="https://github.com/user-attachments/assets/ead1b253-4f78-4ecd-a1d9-c15207c0a249" />

# task 6 : Diagnose and fix three common NGINX errors
Cause a 403 Forbidden: set a file to chmod 600 and try to access it — then fix it.
Cause a 502 Bad Gateway: set proxy_pass to a port with no container running — observe and
fix it.
Cause a config error: remove a closing brace from a server block — run nginx -t to catch it,
then fix it.
For each scenario, write down which log file contained the error and what the exact error
message was.
```bash
# Test 403
sudo chmod 600 /var/www/mysite.local/html/index.html
curl -o /dev/null -s -w '%{http_code}' http://mysite.local
sudo tail -5 /var/log/nginx/error.log
# Test 502
# Change proxy_pass to http://127.0.0.1:9999 (nothing running)
sudo systemctl reload nginx
curl -o /dev/null -s -w '%{http_code}' http://myapp.local
```
<img width="1920" height="1080" alt="web_6 1" src="https://github.com/user-attachments/assets/cefa850e-20af-42a1-a3bb-951ef7f59e4a" />
<img width="1920" height="1080" alt="web_6 2" src="https://github.com/user-attachments/assets/e843471e-a3fd-4bb2-bd1a-2160b3404fa7" />
<img width="1920" height="1080" alt="web_6 3" src="https://github.com/user-attachments/assets/588e374d-774f-449f-ac94-5a5a03d784a7" />
<img width="1792" height="430" alt="web_6 4" src="https://github.com/user-attachments/assets/22c268ad-f78a-4083-b13f-9fb1316974aa" />
