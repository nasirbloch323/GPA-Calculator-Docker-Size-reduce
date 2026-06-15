# 🎓 GPA Calculator
### Streamlit App — Dockerized & Deployed on AWS EC2

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazon-aws&logoColor=white)

> A GPA Calculator built with Streamlit — Containerized with Docker using Alpine for optimized image size and deployed on AWS EC2.

---

## 🌐 Live Demo
```
http://54.175.209.125:8501
```

---

## 📦 Image Size Optimization

| Base Image | Size |
|-----------|------|
| python:3.10-slim | 185MB ❌ |
| python:3.10-alpine | 23MB ✅ |

> **70% size reduction** just by changing base image!

---

## 🛠️ Tech Stack
| Technology | Usage |
|-----------|-------|
| Python | Programming Language |
| Streamlit | Web Framework |
| Docker Alpine | Containerization |
| AWS EC2 | Cloud Deployment |

---

## 🚀 Step-by-Step Deployment

### Step 1: Clone Project
```bash
git clone https://github.com/nasirbloch323/GPA-Calculator.git
cd GPA-Calculator
ls
```

### Step 2: Requirements Banao
```bash
cat > requirements.txt <<EOF
streamlit
EOF
```

### Step 3: Optimized Dockerfile Banao
```bash
nano Dockerfile
```

```dockerfile
# Alpine = Chota Linux = Choti Image ✅
FROM python:3.10-alpine

# Working directory
WORKDIR /app

# Requirements copy karo
COPY requirements.txt .

# Install karo — cache nahi rakho
RUN pip install --no-cache-dir -r requirements.txt

# Sari files copy karo
COPY . .

# Streamlit port
EXPOSE 8501

# App chalao
CMD ["streamlit", "run", "streamlit_gpa.py", \
     "--server.address=0.0.0.0", \
     "--server.port=8501"]
```

### Step 4: Image Build Karo
```bash
docker build -t gpa-calculator .

# Size check karo
docker images
```

### Step 5: Container Chalao
```bash
docker run -d \
--name gpa-app \
-p 8501:8501 \
gpa-calculator
```

### Step 6: Verify Karo
```bash
# Container chal raha hai?
docker ps

# Logs dekho
docker logs gpa-app
```

### Step 7: AWS Security Group
```
EC2 → Security Groups → Inbound Rules:
Port 8501 → Custom TCP → 0.0.0.0/0 ✅
```

### Step 8: Browser Mein Kholo
```
http://YOUR_EC2_IP:8501
```

---

## 💡 Key Learnings
```
✅ Alpine = Smallest base image
✅ --no-cache-dir = Extra space bachao
✅ COPY requirements first = Fast rebuild
✅ EXPOSE = Port document karo
```

---

## 🔧 Useful Commands
```bash
# Container stop karo
docker stop gpa-app

# Container delete karo
docker rm -f gpa-app

# Image delete karo
docker rmi gpa-calculator

# Size check karo
docker images
```

---

*Made with ❤️ by Nasir Baloch — DevOps Journey 🚀*
*github.com/nasirbloch323*
