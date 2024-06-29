## Port Forwarding with Nginx

### Create and Start a New Container:
1. **Create a New Container and Start It with a Custom Name:**
   - `docker run -d --name webserve nginx`
   - `docker run -d --name webserve image:version`

2. **Forward Ports to the Container:**
   - To forward ports from the host machine to the Docker container, use the `-p` option followed by `host_port:container_port`.
   - Example: Forward port 80 from the host to port 80 in the container:
     - `docker run -d --name webserve -p 80:80 nginx`

3. **Forward Multiple Ports:**
   - You can forward multiple ports by specifying multiple `-p` options.
   - Example: Forward ports 80 and 443:
     - `docker run -d --name webserve -p 80:80 -p 443:443 nginx`

### Example Commands for Nginx:

- **Basic Nginx Container with Port Forwarding:**
  - `docker run -d --name webserve -p 80:80 nginx`
- **Nginx Container with Custom Version and Port Forwarding:**
  - `docker run -d --name webserve -p 80:80 -p 443:443 nginx:alpine`

### Verifying the Setup:
1. **Check Running Containers:**
   - `docker ps`
   - Ensure your `webserve` container is running and the ports are forwarded correctly.

2. **Access the Web Server:**
   - Open a web browser and navigate to `http://localhost` or `http://<your-host-ip>` to see the default Nginx welcome page.

3. **Check Container Logs:**
   - To see if Nginx is running properly, check the container logs:
     - `docker logs webserve`

## Managing Docker Containers

### Restarting a Container:
- `docker restart container_name`
- Example: `docker restart webserve`

### Pausing and Unpausing a Container:
- **Pause a Container:**
  - `docker pause container_name`
  - Example: `docker pause webserve`
- **Unpause a Container:**
  - `docker unpause container_name`
  - Example: `docker unpause webserve`

### Executing Commands Inside a Running Container:
- **Run a Command in a Running Container:**
  - `docker exec -it container_name command`
  - Example: Open a bash shell in the running Nginx container:
    - `docker exec -it webserve bash`

## Docker Volumes

### Creating and Using Volumes:
- **Create a Volume:**
  - `docker volume create volume_name`
- **Run a Container with a Volume:**
  - `docker run -d --name container_name -v volume_name:/path/in/container image_name`
  - Example: `docker run -d --name webserve -v web_data:/usr/share/nginx/html nginx`

### Managing Volumes:
- **List Volumes:**
  - `docker volume ls`
- **Remove a Volume:**
  - `docker volume rm volume_name`
- **Inspect a Volume:**
  - `docker volume inspect volume_name`

## Conclusion
This guide covers the basic and advanced usage of Docker commands, from pulling images and running containers to managing logs, ports, and volumes. By following these steps, you can efficiently manage Docker containers and ensure your applications run smoothly in isolated environments.