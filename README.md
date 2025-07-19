<h2>Python Flask App</h2>
This repository consists on how to build a simple Python Flask App.

<h2> Author</h2>
Sean Daweng


<h2> Tech includes Python + Flask <h/2>
<ul>
<li>Tools: python3, flask, docker</li>
<li>Goal: Containerize a basic Flask web app (hello-world API)</li>
<li>Skills: Multi-stage builds, exposing ports, and using requirements.txt.</li>
</ul>

<h2>Repository Structure</h2>
<pre>
docker-beginners-sandbox/
    ├── flask-app/
    |    ├── app.py
    │    ├── requirements.txt
    │    └── Dockerfile
</pre>


<h2>Steps:</h2>

1) Create a structured directories for this simple project
<pre>
mkdir docker-beginners-sandbox
cd docker-beginners-sandbox
mkdir flask-app
vim app.py
vim requirements.txt
vim Dockerfile
</pre>

2) Install python3 with the latest version if you have not installed it yet
<pre>apt install python3</pre>

3) Install flask
<pre>sudo apt install python3-flask -y</pre>

4) Edit app.py file and insert:
get into app.py file by vim app.py
<pre>
from flask import Flask
app = Flask(__name__)

@app.route('/')
def home():
    return "Hello from Dockerized Flask!"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
</pre>
5) Close file and save. (Use :wq)

6) Get into requirements.txt file by vim requirements.txt and add
<pre>Flask==2.3.2</pre>

7) Close file and save. (Use :wq)

8) Edit Dockerfile and add
<pre>
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "app.py"]
</pre>
9) Close file and save. (Use :wq)


10) Build & run
<pre>
cd flask-app
docker build -t flask-sandbox .
docker run -p 5000:5000 flask-sandbox
</pre>
11) Visit http://localhost:5000 in your local browser.
