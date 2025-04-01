---
lang: en
title: Deployment
viewport: width=device-width, initial-scale=1.0
---

# HERConnect Chatbot Project Deployment Documentation

## Deployment Overview

The application is deployed in a Docker container hosted on a Cybera Ubuntu 22.0.4 instance. This deployment strategy with containerized approach, ensures ease of migration to various hosting services or instances, catering to the diverse infrastructure requirements and preferences of the client.

## Deployment Instructions

### 1. Prepare the Environment

- **Install Docker**: Ensure Docker is installed on your instance for containerization of the application components. _For more information, see [Docker Engine installation documentation](https://docs.docker.com/engine/install/)._

> **Note:** Note that the installation process may vary for different operating systems. Refer to the official documentation for detailed instructions.

> **Note:** These installations are essential for running the application on your own server and should be completed before proceeding with the application setup.

### 2. Access the Application Repository

To deploy the application, you need access to its source code, typically stored in a GitHub repository. Before you can clone the repository, make sure Git is installed on your machine.

#### Install Git
1. **Open a Terminal**: On your machine, open a terminal window.
2. **Install Git**: Follow the installation instructions based on your operating system. You can find detailed installation instructions in [Git's official documentation](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

#### Clone the Repository
   1. **Generate an SSH key**: Running the following command in the root directory:
     
    ```bash
    ssh-keygen
    ```

   2. **Copy public key**: Run the following command to display the public key and copy it to the clipboard:

    ```bash
    cat ~/.ssh/id_rsa.pub
    ```

   3. **Add public key under Github account**: Open the GitHub repository and navigate to `Settings` -> `SSH and GPG keys` -> `New SSH key`. Paste the public key into the key field.

   4. **Set permissions**: Running the following command to set the permissions for the SSH key:
    ```bash
    chmod 600 ~/.ssh/id_rsa
    ```

   5.  **clone the repository**: Navigate to the desired directory and clone the repository using the following command:

    ```bash
    git clone git@github.com:UAlberta-CMPUT401/w24project-abtn_herconnect.git
    ```
   


### 3. Finalizing the Deployment

After cloning the repository, the next step is to set up the application environment and get it running on your server. This is streamlined with the `setup-environment.sh` script provided in the repository.

#### Environment Configuration

1. **Prepare `.env` file**: On root directory of the repository, run the following script. This script will generate *Django Secret Key* and store it in the `/backend/chatbot_api/chatbot/.env` file.

    ```bash
     chmod +x generate-env.sh
    ./generate-env.sh
    ```

2. **Configure environment variables**: Edit the `/backend/chatbot_api/chatbot/.env` file to include your email credentials which the chatbot will use for sending emails. Replace `example@example.com` and `password` with your actual email address and password.

    ```plaintext
    HERBOT_EMAIL_HOST_USER='example@example.com'
    HERBOT_EMAIL_HOST_PASSWORD='password'
    ```

> **Note:** This configuration is essential for enabling the automated email forwarding functionality.

#### Build and run the Docker containers
   Navigate to the root directory of the repository and run the `setup-environment.sh` script. This script will build the Docker containers and start the application.

  ```bash
  chmod +x setup-environment.sh
  ./setup-environment.sh
  ```
#### Access the Application

  Once the `setup-environment.sh` script has completed its execution, the application components should be up and running. You can access them as follows:

- **Chatbot Interface**: 
  Access the chatbot on your server by navigating to `/wordpress`. For example, if your server IP is ` http://your_server_ip`, you can access the chatbot at `http://your_server_ip/wordpress`.
  
- **Admin Page**: 
  To manage the chatbot settings, access the admin page at `/login`.

> **Note:** For more detailed instructions, configurations, please refer to the `README.md` file in the repository.


## Technical Details

### Frontend
- **Technology**: WordPress plugin
- **Languages**: PHP, HTML, CSS, JavaScript

### Backend
- **Framework**: Django
- **Database**: SQLite3

### Deployment Environment
- **Containerization**: Docker
- **Web Server**: Nginx

## Required Libraries

> **Note:** The following libraries are essential for the application, but you **do not** need to manually install them. They are automatically included and managed during the deployment process:

- certifi==2024.2.2
- charset-normalizer==3.3.2
- greenlet==3.0.3
- idna==3.6
- iniconfig==2.0.0
- packaging==23.2
- playwright==1.41.2
- pluggy==1.4.0
- pyee==11.0.1
- pytest==8.0.1
- pytest-base-url==2.1.0
- pytest-playwright==0.4.4
- python-slugify==8.0.4
- requests==2.31.0
- text-unidecode==1.3
- typing_extensions==4.9.0
- urllib3==2.2.1
- asgiref==3.7.2
- Django==4.2.10
- django-js-asset==2.2.0
- django-mptt==0.16.0
- djangorestframework==3.14.0
- pytz==2024.1
- sqlparse==0.4.4
- typing_extensions==4.9.0
- drf-spectacular==0.27.1
- django-cors-headers==4.3.1
- emoji==2.10.1
- python-dotenv==1.0.1




