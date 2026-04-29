# Docker Container Registry Practice

A simple Flask app to practice pushing/pulling Docker images via Docker Hub and GitHub Container Registry (GHCR).

---

## 📁 Project Structure

```
├── Dockerfile
├── app.py
├── requirements.txt
├── .dockerignore
└── README.md
```

---

## 🐳 Option A: Docker Hub

### Step 1 — Build the image
```bash
docker build -t my-flask-app .
```

### Step 2 — Login to Docker Hub
```bash
docker login
```
Enter your Docker Hub username and password.

### Step 3 — Tag the image
```bash
docker tag my-flask-app YOUR_DOCKERHUB_USERNAME/my-flask-app:v1
```

### Step 4 — Push to Docker Hub
```bash
docker push YOUR_DOCKERHUB_USERNAME/my-flask-app:v1
```

### Step 5 — Pull and run
```bash
docker pull YOUR_DOCKERHUB_USERNAME/my-flask-app:v1
docker run -p 5000:5000 YOUR_DOCKERHUB_USERNAME/my-flask-app:v1
```
Visit: http://localhost:5000

---

## 🐙 Option B: GitHub Container Registry (GHCR)

### Step 1 — Generate a Personal Access Token (PAT)
- Go to GitHub → Settings → Developer Settings → Personal Access Tokens → Tokens (classic)
- Enable scopes: `write:packages`, `read:packages`
- Copy the token

### Step 2 — Login to GHCR
```bash
echo YOUR_TOKEN | docker login ghcr.io -u YOUR_GITHUB_USERNAME --password-stdin
```

### Step 3 — Build the image
```bash
docker build -t ghcr.io/YOUR_GITHUB_USERNAME/my-flask-app:v1 .
```

### Step 4 — Push to GHCR
```bash
docker push ghcr.io/YOUR_GITHUB_USERNAME/my-flask-app:v1
```

### Step 5 — Pull and run
```bash
docker pull ghcr.io/YOUR_GITHUB_USERNAME/my-flask-app:v1
docker run -p 5000:5000 ghcr.io/YOUR_GITHUB_USERNAME/my-flask-app:v1
```
Visit: http://localhost:5000

---

## 🧠 Worksheet Answers

**Q1. What is a container registry?**  
A centralized storage service for Docker images — like GitHub but for containers.

**Q2. Why do we push images to a registry?**  
To share images across machines and teams, and to enable consistent deployment in CI/CD.

**Q3. What is the role of tagging?**  
Tags identify specific versions of an image (e.g., `v1`, `latest`) and link a local image to its registry path.

**Q4. What problems are solved by container registries?**  
Version control for images, team collaboration, reproducible deployments, and integration with CI/CD pipelines.
