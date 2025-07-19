Python Flask App
----------------------------------------------------------------------
Tech: Python + Flask
Goal: Containerize a basic Flask web app (hello-world API)
Skills: Multi-stage builds, exposing ports, and using requirements.txt.

----------------------------------------------------------------------
Repository Structure
docker-beginners-sandbox/
├── flask-app/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile

----------------------------------------------------------------------

Steps:
1) Create directory for this simple project

mkdir docker-beginners-sandbox
cd docker-beginners-sandbox
mkdir flask-app
vim app.py
vim requirements.txt
vim Dockerfile

2) Install python3 with the latest version if you have not installed it yet
apt install python3

3) Install flask
sudo apt install python3-flask -y

4) Edit app.py file and insert:

from flask import Flask
app = Flask(__name__)

@app.route('/')
def home():
    return "Hello from Dockerized Flask!"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)

5) Close file and save

6) Edit requirements.txt file:
Flask==2.3.2

7) Close file and save

8) Edit Dockerfile

FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "app.py"]

9) Close file and save


10) Build & run

cd flask-app
docker build -t flask-sandbox .
docker run -p 5000:5000 flask-sandbox

11) Visit http://localhost:5000 in your local browser.
