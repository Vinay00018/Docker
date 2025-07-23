# Docker
🚢 What is Docker?
Docker is a containerization platform
Docker is a tool used to package your application and everything it needs (code, libraries, environment) into a container.

🧱 Key Concepts:
| Term         | Meaning                            |
|--------------|-------------------------------------|
| Image        | Blueprint for container             |
| Container    | Running instance of image           |
| Dockerfile   | File to define an image             |
| Docker Hub   | Public repo for Docker images       |

🛠️ How Docker Works
You create an image from a Dockerfile
Run a container from the image
Containers use host machine resources

📦 What is a Container?
A container is a lightweight, isolated environment to run your application.
It's like a mini virtual machine, but faster and uses less memory.

🛠️ Why Use Docker?
Works anywhere – "It runs on my machine" problem is solved.
Lightweight & Fast – starts quickly.
Portable – move it between servers/cloud easily.
Easy to scale – great for microservices.

<img width="921" height="494" alt="image" src="https://github.com/user-attachments/assets/16381be3-2d17-4a96-bfbf-68f2a9954d89" />

✅ Docker uses client-server architecture.
👤 Client: You (via terminal) run commands like docker run, docker build.
⚙️ Docker Daemon (Server): Does the actual work – builds images, runs containers.
🔁 They communicate using a REST API.
🖥️ Docker Host: Machine where daemon is running (local or cloud like EC2).
☁️ Registry: Stores Docker images (e.g., Docker Hub).
📦 Client pulls images from registry → Daemon runs them as containers

********* by default the file must be named Dockerfile *****

| Command      | What it does                                                               |
| ------------ | -------------------------------------------------------------------------  |
| `FROM`       | ✅ Base image (must be first line)                                         |
| `WORKDIR`    | ✅ Set working directory inside container                                  |
| `COPY`       | ✅ Copy files from host to container                                       |
| `RUN`        | ✅ Run command during **build time**                                       |
| `CMD`        | ✅ Command to run at **container start**                                   |
| `EXPOSE`     | Inform Docker what port app uses (e.g., `EXPOSE 5000`)                     |

 1. FROM – Base image
FROM python:3.10
 2. WORKDIR – Set working directory inside container
WORKDIR /app
 3. COPY – Copy files from local machine to container
COPY . .
 4. RUN – Run commands during image build (e.g., install packages)
RUN pip install -r requirements.txt
 5. CMD – Default command to run when container starts
CMD ["python", "app.py"]
6. EXPOSE – Inform Docker which port app uses
EXPOSE 5000
 7. ENV – Set environment variables inside container
ENV ENVIRONMENT=production

🔧 Docker Installation (simple):

sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker $USER
🔍 Check Docker version:
docker --version

🛠️ Build Docker Image (-t is tag simpleapp is imagename and (.)is a directory if dockerfile in same folder use . else use ./pathname)
docker build -t simpleapp .

📋 List all local Docker images
docker images

▶️ Run a container from the image (-d is deamon mode and -p is port first dockerport:second vm port )
docker run -d -p 8000:8000 simpleapp

📦 Show running containers
docker ps

📦 Show all containers (running + stopped)
docker ps -a

🌐 Push to Docker Hub
docker login                                      (to login to docker hub website)
docker tag simpleapp yourusername/simpleapp        (tag to create name path in dockerhub)
docker push yourusername/simpleapp                  (to push iamge to dockerhub)

🌐To pull an image from Docker Hub
docker pull username/image-name                      (to pull image from docker hub to vm)
