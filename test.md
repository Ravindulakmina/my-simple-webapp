# Simple Web Application

This is a simple web application using [Python Flask](http://flask.pocoo.org/)

Below are the steps required to get this working on a base linux system.

- **Install all required dependencies**
- **Install and Configure Web Server**
- **Start Web Server**

## 1. Install all required dependencies

Python and its dependencies

```bash
apt update && apt install -y python3 python3-pip
```

## 2. Install and Configure Web Server

Install Python Flask dependency

```bash
pip3 install flask

```

- Copy `app.py` or download it from a source repository
- Configure database credentials and parameters

## 3. Start Web Server

Start web server

```bash
FLASK_APP=app.py flask run --host=0.0.0.0
```

## 4. Test

Open a browser and go to URL

```
http://<IP>:5000                            => Welcome
http://<IP>:5000/how%20are%20you            => I am good, how about you?
```

Create docker Image

```bash
cd my-simple-webapp/
```

```bash
nano Dockerfile
```

```bash
docker build .
```

```bash
docker build . -t my-simple-webapp

````

```bash
docker images
````

```bash
docker images
```

```bash
 docker run -p 5000:5000 my-simple-webapp
```

Push docker image
```bash
docker login
docker build . -t ravindulakmina/my-simple-webapp
docker images
docker push ravindulakmina/my-simple-webapp
```