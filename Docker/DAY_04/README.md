# Docker Day 4 – Volumes and Networking

## Objective
The objective of this task is to understand Docker volumes for persistent storage and Docker networking for communication between containers.

---

# 1. Named Volume

Create a Docker volume:
```bash
docker volume create myvolume
```

Screenshot:

![Create Volume](screenshots/create_volume.png)


Run container using the volume:
```bash
docker run -d --name volume-container -v myvolume:/app/data nginx
```

Screenshot:

![Container With Volume](screenshots/container_with_volume.png)


Add data inside container:
```bash
docker exec -it volume-container bash
cd /app/data
echo "Docker Volume Test" > file.txt
```

Screenshot:

![Data Inside Container](screenshots/data_inside_container.png)

```bash
Remove container and run again to verify persistence:
```

Screenshot:

![Volume Persistence](screenshots/remove_container_again_run.png)

---

# 2. Bind Mount


Create directory on host:
```bash
mkdir bind-data
```
Run container with bind mount:

```bash
docker run -d --name bind-container -p 8080:80 -v $(pwd)/bind-data:/usr/share/nginx/html nginx

```

Screenshot:

![Bind Mount](screenshots/bind-mount.png)


Create webpage:
```bash
echo "<h1>Bind Mount Working</h1>" > bind-data/index.html
```

Screenshot:

![Bind Mount Webpage](screenshots/bind_mount_webpage.png)

# Output:

![Bind Mount Working](screenshots/bind_mount_working.png)

---

# 3. Anonymous Volume

Run container with anonymous volume:

```bash
docker run -d --name anon-container -v /app/data nginx
```

![Anonymous Volume](screenshots/anonymous_volume.png)



# 4. Persist Database Data Using Volume

Run MySQL container with volume:
```bash
docker run -d
--name mysql-container
-e MYSQL_ROOT_PASSWORD=root
-v mysql-data:/var/lib/mysql
mysql:5.7
```

Screenshot:

![MySQL Persistence](screenshots/persiste_data_mysql.png)



# 5. Create Custom Docker Network

Create network:
```bash
docker network create mynetwork
```

Screenshot:

![Docker Custom Network](screenshots/docker_custom_network.png)

---

# 6. Connect Multiple Containers

Run containers in the same network:
```bash
docker run -dit --name container1 --network mynetwork nginx
docker run -dit --name container2 --network mynetwork busybox
```

Screenshot:

![Connecting Containers](screenshots/connecting_multiple_container.png)


Test communication:
```bash
docker exec -it container2 sh
ping container1
```

---

# 7. Inspect Docker Network


Inspect network details:
```bash
docker network inspect mynetwork
```

Screenshot:

![Inspect Network](screenshots/inspect_mynetwork.png)

---

# Conclusion
```bash
In this task we successfully implemented:

- Named Volumes
- Bind Mounts
- Anonymous Volumes
- Database Persistence using Docker Volumes
- Custom Docker Networks
- Container-to-Container Communication
- Docker Network Inspection
```