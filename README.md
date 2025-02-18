Here's a refined version of your `README.md` file, providing clear instructions and formatting. This includes Docker-specific steps and ensures everything is laid out properly for easy understanding.

---

# Simple Web Application

This is a simple web application using [Python Flask](http://flask.pocoo.org/).

Below are the steps required to get this working on an Ubuntu operating system (VPS).

## Steps to Set Up

1. **Install all required dependencies**
2. **Install and Configure Web Server**
3. **Start Web Server**
4. **Test**
5. **Create Docker Image**
6. **Push Docker Image**

---

## 1. Install All Required Dependencies

Ensure your system has Python and pip installed:

```bash
apt update && apt install -y python3 python3-pip
```

---

## 2. Install and Configure Web Server

Next, install the Python Flask dependency:

```bash
pip3 install flask
```

- Copy `app.py` or download it from your source repository.
- Configure any necessary database credentials and parameters within your `app.py`.

---

## 3. Start Web Server

Start the Flask web server by running:

```bash
FLASK_APP=app.py flask run --host=0.0.0.0
```

---

## 4. Test

Open a browser and visit the following URLs to test the web application:

```
http://<IP>:5000                          => Welcome
http://<IP>:5000/how%20are%20you          => I am good, how about you?
```

---

## 5. Create Docker Image

To containerize the web application using Docker, follow these steps:

### 1. Navigate to your project folder:

```bash
cd my-simple-webapp/
```

### 2. Create the `Dockerfile`:

```bash
nano Dockerfile
```

Add the following content to your `Dockerfile` (if not already added):

```dockerfile
# Use an official Python runtime as a base image
FROM python:3.12

# Set the working directory inside the container
WORKDIR /opt

# Install system dependencies
RUN apt-get update && apt-get install -y python3 python3-pip python3-venv

# Create and activate a virtual environment
RUN python3 -m venv venv

# Install Flask within the virtual environment
RUN /opt/venv/bin/pip install --upgrade pip && /opt/venv/bin/pip install flask

# Copy the application files
COPY app.py /opt/app.py

# Expose the Flask default port
EXPOSE 5000

# Run the Flask app inside the virtual environment
CMD ["/opt/venv/bin/python", "-m", "flask", "run", "--host=0.0.0.0"]
```

### 3. Build your Docker image:

```bash
docker build . -t my-simple-webapp
```

---

## 6. Push Docker Image

Once the Docker image is built, push it to your Docker Hub repository:

### 1. Log in to Docker Hub:

```bash
docker login
```

### 2. Tag your image:

```bash
docker build . -t ravindulakmina/my-simple-webapp
```

### 3. Push the image to Docker Hub:

```bash
docker push ravindulakmina/my-simple-webapp
```

---

That's it! You've successfully created, tested, and pushed your web app to Docker Hub.

Let me know if you need further clarifications or adjustments! 🚀