# Docker Day 03 – Volumes and Networking

## 1. Practical Implementation of Docker Volumes

### Step 1: Create a Docker Volume

```bash
docker volume create swiggy
```

This command creates a Docker volume named **swiggy** which will store persistent data.

---

### Step 2: Inspect the Volume

```bash
docker volume inspect swiggy
```

This command displays detailed information about the volume such as:

* Mountpoint location
* Creation time
* Driver type

Example Mountpoint:

```
/var/lib/docker/volumes/swiggy/_data
```

This directory is where Docker stores volume data on the host machine.

---

### Step 3: Mount the Volume to a Container

```bash
docker run -itd --name cont1 --mount src=swiggy,destination=/myapp ubuntu
```

Explanation:

* `-itd` → Runs container in interactive + detached mode
* `--name cont1` → Container name
* `--mount` → Mounts Docker volume
* `src=swiggy` → Source volume
* `destination=/myapp` → Mount point inside container

This attaches the **swiggy volume** to the **/myapp directory** inside the container.

---

### Step 4: Access the Running Container

```bash
docker exec -it cont1 /bin/bash
```

Inside the container check the mounted directory:

```bash
ls /
```

You should see the **myapp directory**.

---

# 2. Introduction to Docker Networking

Docker networking allows containers to communicate with:

* Other containers
* Host machine
* External networks (Internet, APIs)

It helps in:

* Container-to-container communication
* Internet access
* Exposing services
* Security and isolation

---

# 3. Types of Docker Networks

Docker provides five major network drivers:

1. Bridge Network
2. Host Network
3. None Network
4. Overlay Network
5. Macvlan Network

---

## 3.1 Bridge Network (Default)

Default network created when Docker is installed.

Features:

* Provides container isolation
* Containers get internal IP addresses
* Allows outbound internet access

Example:

```bash
docker run -d --name my-bridge-app nginx
```

External access requires **port mapping (-p)**.

---

## 3.2 Host Network

Container shares host’s network.

Example:

```bash
docker run -d --network host --name my-host-app nginx
```

Features:

* No port mapping needed
* Uses host IP directly
* High performance

---

## 3.3 None Network

Container has **no network access**.

Example:

```bash
docker run -d --network none --name my-none-app nginx
```

Useful for **offline processing or batch jobs**.

---

## 3.4 Overlay Network

Used for communication across **multiple Docker hosts**.

Example:

```bash
docker network create -d overlay my-overlay-net
```

Run service:

```bash
docker service create --name my-overlay-app --network my-overlay-net nginx
```

Requires **Docker Swarm**.

---

## 3.5 Macvlan Network

Assigns a **real MAC address** to the container.

Example:

```bash
docker network create -d macvlan \
--subnet=192.168.1.0/24 \
--gateway=192.168.1.1 \
-o parent=eth0 my-macvlan-net
```

Run container:

```bash
docker run -d --network my-macvlan-net --name my-macvlan-app nginx
```

Container behaves like a **physical device on the network**.

---

# 4. Creating a Custom Docker Network

### Step 1: List Networks

```bash
docker network ls
```

---

### Step 2: Create Network

```bash
docker network create my-app-network
```

---

### Step 3: Run Containers on Network

```bash
docker run -d --name web-server-1 --network my-app-network nginx
docker run -d --name web-server-2 --network my-app-network nginx
```

---

### Step 4: Inspect Network

```bash
docker network inspect my-app-network
```

Shows:

* Connected containers
* IP addresses
* Network configuration

---

### Step 5: Test Container Communication

```bash
docker exec -it web-server-1 curl http://web-server-2
```

If successful, container **web-server-1 communicates with web-server-2**.

---

