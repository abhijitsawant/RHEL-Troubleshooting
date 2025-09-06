<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8"/>
  <meta name="viewport" content="width=device-width,initial-scale=1"/>
  <title>Docker & Docker Compose Guide</title>
  <style>
    body { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Arial; line-height:1.5; padding:24px; color:#111; }
    pre { background:#f6f8fa; padding:12px; border-radius:6px; overflow:auto; }
    code { font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, "Roboto Mono"; }
    h1,h2,h3 { margin-top:1.2em; }
    nav ul { list-style: none; padding-left:0; }
    nav li { margin:6px 0; }
  </style>
</head>
<body>

  <h1>Docker & Docker Compose Guide</h1>
  <p>This README provides commonly used Docker and Docker Compose commands, including how to check local and remote images.</p>

  <h2>Table of Contents</h2>
  <nav>
    <ul>
      <li><a href="#docker-basics">Docker Basics</a></li>
      <li><a href="#image-management">Image Management</a></li>
      <li><a href="#container-management">Container Management</a></li>
      <li><a href="#logs-exec">Logs & Exec</a></li>
      <li><a href="#networks-volumes">Networks & Volumes</a></li>
      <li><a href="#docker-hub">Docker Hub</a></li>
      <li><a href="#docker-images">Check Available Images</a></li>
      <li><a href="#docker-compose">Docker Compose</a></li>
      <li><a href="#docker-compose-example">Example docker-compose.yml</a></li>
    </ul>
  </nav>

  <hr/>

  <h2 id="docker-basics">Docker Basics</h2>
  <pre><code>docker --version           # Check Docker version
docker info                # System-wide info
docker system df           # Disk usage by images/containers
docker system prune        # Clean up unused objects</code></pre>

  <h2 id="image-management">Image Management</h2>
  <pre><code>docker images                  # List local images
docker pull ubuntu:20.04       # Pull image from Docker Hub
docker rmi &lt;image_id&gt;          # Remove an image
docker build -t myapp:1.0 .    # Build image from Dockerfile
docker tag myapp:1.0 user/myapp:1.0   # Tag image for repo
docker push user/myapp:1.0     # Push to Docker Hub</code></pre>

  <h2 id="container-management">Container Management</h2>
  <pre><code>docker ps                       # List running containers
docker ps -a                    # List all containers
docker run -it ubuntu bash      # Start container with shell
docker run -d --name web nginx  # Run detached container
docker stop &lt;id&gt;                # Stop container
docker start &lt;id&gt;               # Start stopped container
docker restart &lt;id&gt;             # Restart container
docker rm &lt;id&gt;                  # Remove container</code></pre>

  <h2 id="logs-exec">Logs & Exec</h2>
  <pre><code>docker logs &lt;id&gt;            # View logs
docker logs -f &lt;id&gt;         # Follow logs
docker exec -it &lt;id&gt; bash   # Access container shell</code></pre>

  <h2 id="networks-volumes">Networks & Volumes</h2>
  <pre><code>docker network ls           # List networks
docker network create mynet # Create network
docker volume ls            # List volumes
docker volume create myvol  # Create volume</code></pre>

  <h2 id="docker-hub">Docker Hub</h2>
  <pre><code>docker login                # Authenticate
docker logout               # Logout
docker push user/myapp:1.0  # Push image</code></pre>

  <h2 id="docker-images">Check Available Images</h2>
  <p>👉 Check locally installed images:</p>
  <pre><code>docker images</code></pre>
  <p>👉 Search Docker Hub for available images:</p>
  <pre><code>docker search nginx
docker search postgres</code></pre>

  <h2 id="docker-compose">Docker Compose</h2>
  <pre><code>docker compose version       # Check version
docker compose up            # Start services (foreground)
docker compose up -d         # Start in background
docker compose down          # Stop & remove
docker compose ps            # List running services
docker compose logs -f       # View logs
docker compose build         # Rebuild services
docker compose restart       # Restart services</code></pre>

  <h2 id="docker-compose-example">Example docker-compose.yml</h2>
  <pre><code>version: '3.9'
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
  db:
    image: postgres:13
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: pass
      POSTGRES_DB: appdb
    volumes:
      - db_data:/var/lib/postgresql/data
volumes:
  db_data:</code></pre>

  <hr/>
  <p><em>End of Docker Guide</em></p>

</body>
</html>
