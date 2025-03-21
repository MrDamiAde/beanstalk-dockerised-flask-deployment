# Beanstalk Dockerised Flask Deployment

This project demonstrates my ability to deploy a Flask application on AWS Elastic Beanstalk using Docker and set up SSL to secure the web app with ACM.

## Key Technologies Used

- **AWS Elastic Beanstalk**
- **Docker**
- **AWS CLI**
- **EB CLI**
- **AWS Certificate Manager (ACM)**
- **GitHub**
- **Python (Flask)**
- **Bash**

## 1. Creating the Flask App

I built a simple Flask application with a single route to demonstrate deployment on AWS. The app serves basic HTTP responses and includes a `requirements.txt` file for dependency management.

Here is the screenshot of the app locally:

![App Screenshot](screenshots/Screenshot%202025-03-19%20121113.png)


### Files:
- `app.py` – Main Flask application
- `requirements.txt` – Dependencies

## 2. Dockerising the Flask App
I containerised the application using Docker to ensure portability and consistency across environments.

### Steps:
1. Created a `Dockerfile` with a lightweight `python:3.x` base image.
2. Installed dependencies and copied the Flask app into the container.
3. Exposed the necessary port (`5000`) and defined the startup command.

Here is the screenshot of the dockerised app being launched on localhost:

![App Screenshot2](screenshots/Screenshot%202025-03-19%20124048.png)
=

### Key Files:
- `Dockerfile`
- `.dockerignore`

## 3. Deploying to AWS Elastic Beanstalk with SSL
I used AWS Elastic Beanstalk to deploy the Docker container and secured it using SSL via ACM.

### Steps:
1. Configured an Elastic Beanstalk environment with Docker.
2. Used `eb init` and `eb create` to deploy the app.
3. Bought a domain and configured the subdomain 'app.damiadeprojects.uk'
4. Requested and attached an SSL certificate from ACM.

![App Screenshot](screenshots/Screenshot%202025-03-21%20090345.png)<br>

6. Updated the load balancer settings to enforce HTTPS.

![App Screenshot](screenshots/Screenshot%202025-03-21%20092724.png)

Here is screenshot of the my secured web app running via Beanstalk:

![App Screenshot](screenshots/Screenshot%202025-03-21%20092501.png)


### Key Commands:
- `eb init` – Initialise the Elastic Beanstalk project.
- `eb create my-app-env` – Deploy the application.
- `aws acm request-certificate` – Request an SSL certificate.
- `eb config` – Update environment settings for HTTPS enforcement.

