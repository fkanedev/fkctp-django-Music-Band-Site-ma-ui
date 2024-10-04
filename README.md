![Python 3.9](https://img.shields.io/badge/Python-3.9-blue.svg)
![Built with Django](https://img.shields.io/badge/Built%20with-Django-brightgreen.svg)
![Authentication - Django](https://img.shields.io/badge/Authentication-Django-blue.svg)
![Session Management - Django](https://img.shields.io/badge/Session%20Management-Django-orange.svg)
![Cloud Platforms - IBM Cloud](https://img.shields.io/badge/Cloud%20Platforms-IBM%20Cloud-blue.svg)
![Cloud Platforms - Redhat OpenShift](https://img.shields.io/badge/Cloud%20Platforms-Redhat%20OpenShift-red.svg)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)

# Music Band Website
This project aims to develop a Django-based web application for a popular music band. The website allows users to view pictures from past events, see popular lyrics, list upcoming events, create an account, sign in, and register for events. It demonstrates the practical application of Django in a real-world scenario. It's part of my training in the [IBM Developer Skills Network - Back-end Development Capstone](https://github.com/ibm-developer-skills-network/sfvih-Back-end-Development-Capstone) utilizing a [template](https://github.com/ibm-developer-skills-network/sfvih-Back-end-Development-Capstone) provided by IBM Developer Skills Network.

# Topics
`Django`, `Python`, `Web Application`, `Music Band`, `User Authentication`, `Event Management`, `Picture Gallery`, `Song Lyrics`, `Flask`, `MongoDB`, `IBM Cloud`, `Redhat OpenShift`, `SQLite`, `REST API`, `Kubernetes`, `Capstone Project`, `Back-end Development`, `Cloud Deployment`, `Microservices`, `Bootstrap`, `IBM Developer Skills Network`

## Table of Contents
1. [Introduction](#introduction)
2. [Architecture](#architecture)
3. [Technologies Used](#technologies-used)
4. [Installation and Configuration](#installation-and-configuration)
5. [Usage](#usage)
6. [Development](#development)
   - Project Structure
   - Templates
   - Views
   - Models
   - Proxy Services
7. [Deployment](#deployment)
8. [Sources](#sources)
9. [License](#license)
10. [Contact](#contact)

## 1. Introduction <a name="introduction"></a>

### Project Objective
The primary objective of this project is to develop a comprehensive website for a music band using the Django framework. The system facilitates viewing pictures, song lyrics, upcoming events, user interactions, and registrations through a user-friendly web interface. The project integrates [Pictures](https://github.com/fkanedev/fkctp-flask-Pictures-ms) and [Songs](https://github.com/fkanedev/fkctp-flask-Song-ms) microservices built with Flask and MongoDB to manage picture data and song lyrics, demonstrating the practical implementation and utilization of these technologies in a real-world scenario.


### Key Features
- **`Pictures Gallery`** : View pictures from past concerts.
- **`Song Lyrics`** : View popular lyrics of songs.
- **`Upcoming Events`** : See a list of upcoming events.
- **`User Registration`** : Create an account.
- **`Event Registration`** : Sign in and register for an event.
- **`Past Registrations`** : View past event registrations.

## 2. Architecture <a name="architecture"></a>
- **Flask Microservices** : Already developed for the [Get Pictures](https://github.com/fkanedev/fkctp-flask-Pictures-ms) and [Get Songs services](https://github.com/fkanedev/fkctp-flask-Song-ms).
- **MongoDB** : Used for storing song lyrics.
- **Django Application** : Manages the main application functionalities and user interactions.
- **SQLite** : Used for local development and testing of the Django application.
- **IBM Cloud and Redhat OpenShift** : Platforms for deploying microservices and the main application.

## 3. Technologies Used <a name="technologies-used"></a>

### Programming Languages
- **Python**: The core language used for backend development with Django and Flask.

### Tools and Frameworks
- **Django**: A high-level Python web framework.
- **Flask**: A micro web framework for Python.
- **Bootstrap** : Utilized for responsive front-end design.
- **SQLite**: A lightweight, disk-based database for local development.
- **MongoDB**: A NoSQL database for storing song lyrics.

### Cloud Platforms
- **IBM Cloud**: Used for deploying the Get Pictures microservice on IBM Code Engine.
- **Redhat OpenShift**: Used for deploying the Get Songs microservice and MongoDB.
- **IBM Kubernetes Service**: Used for deploying the main application.

## 4. Installation and Configuration <a name="installation-and-configuration"></a>

### Prerequisites
- Ensure that you have Python 3.x and Pip installed.
- Sign up for IBM Cloud and Redhat OpenShift accounts.

### Installation Steps
1. **Clone the repository**:
    ```sh
    git clone https://github.com/fkanedev/fkctp-django-Music-Band-Site-ma-ui
    cd fkctp-django-Music-Band-Site-ma-ui
    ```
2. **Set up the Django server**:
    ```sh
    cd django_concert
    pip install -r requirements.txt
    python manage.py makemigrations
    python manage.py migrate
    python manage.py runserver
    ```
3. **Create an admin user**:
    ```sh
    python manage.py createsuperuser
    ```

## 5. Usage <a name="usage"></a>
### Anonymous Use Cases
- User visits the Django Website home page.
- The song page shows songs and lyrics.
- The pictures page shows pictures from past concerts.

### Admin Use Cases
- Let the admin user change the concert date.

### Signed-in Use Cases
- The user signs into the application.
- The user is able to see their concerts.
- The user is able to book a concert.
- The user is able to delete their reservation.

## 6. Development <a name="development"></a>
### Project Structure 
- **django_concert/** : The main Django project directory containing settings and configurations.
- **concert/** : Contains the core application responsible for concert-related functionalities.
- **static/** : Holds static files such as CSS and JavaScript.
- **templates/** : Contains HTML templates for rendering web pages.

### Templates
- **index.html** : Home page with Djirection Music band presentation.
- **concerts.html** : Presents the concerts list in a Bootstrap table, with attributes (ID, Date, Concert name,...) for each concert.
- **concert_detail.html** : Page showing details of a user’s concert.
- **songs.html** : Page showing a list of songs and lyrics.
- **photos.html** : Page showing a gallery of past concert pictures.
- **login.html** : User login page.
- **signup.html** : User registration page.

### Views
- **index** : Renders the home page.
- **songs** : Retrieve songs from a REST endpoint of [Songs microservice](https://github.com/fkanedev/fkctp-flask-Song-ms) deployed on Redhat OpenShift and renders the song lyrics page.
- **photos** : Retrieve pictures from a REST endpoint of [Pictures microservice](https://github.com/fkanedev/fkctp-flask-Pictures-ms) deployed on IBM Code Engine and renders the pictures gallery.
- **login** : Handles user login.
- **signup** : Handles user registration.
- **concerts** : Renders the user’s concerts.
- **concert_attendee** : Allows users to book a concert.
- **concert_detail** : Renders details of a user’s concert.

### Models
- **Concert** : Represents a concert event with attributes for name, duration, city, and date.
- **User** : Built-in Django user model for authentication.
- **ConcertAttending:** Manages the relationship between users and concerts, indicating whether a user is attending. It includes choices for attendance status and ensures a unique combination of concert and user.
- **Photo:** Represents a photo from a past concert, including URL and event details. This model is not managed by Django's ORM.
- **Song:** Represents a song with its title and lyrics. This model is also not managed by Django's ORM.

## 7. Deployment <a name="deployment"></a>
The deployment process involves several key steps to ensure the successful deployment of microservices for this project:

- **Get Pictures Microservice**:
  - Deployed to IBM Code Engine.
    - Start Code Engine.
    - Clone GitHub Repository.
    - Build Docker Image.
    - Push Image to Registry.
    - Deploy Application.

- **Get Songs Microservice and MongoDB**:
  - Deployed to Redhat OpenShift.
    - Install MongoDB on OpenShift.
    - Clone GitHub Repository.
    - Build and Deploy Application.

### Deploying Main Application

- **Main Application**:
  - Deployed to IBM Kubernetes Service.
    - Setup Kubernetes environment.
    - Configure Docker images.
    - Deploy application containers.

## 8. Sources <a name="sources"></a>
- **Template**: [IBM Developer Skills Network - Back-end Development Capstone](https://github.com/ibm-developer-skills-network/sfvih-Back-end-Development-Capstone)

- **Useful links**:
  - **[Back-end Application Development Capstone Project](https://www.coursera.org/learn/backend-development-capstone-project/home/module/3)**
  - **[IBM Back-End Development Professional Certificate](https://www.coursera.org/professional-certificates/ibm-backend-development)**

## 9. License <a name="license"></a>
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 10. Contact <a name="contact"></a>
### Contact Information

- Send me email :
**fkanecloudtech@gmail.com**
- Connect with me on [LinkedIn](https://www.linkedin.com/in/fkanecloudtech/)
- Visit my [portfolio](https://fkanedev.github.io) to explore my projects and services.

### Contribution and Support
Contributions are welcome. Please refer to the [CONTRIBUTING](CONTRIBUTING.md) file for more information on how to contribute.
