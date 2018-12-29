# Recipe App API
This project provides a simplre recipe API based on the Djanga Rest Framework.

## How to run the app on a local machine

**Installing Docker**

macOS and Windows users can install [Docker Desktop](https://www.docker.com/products/docker-desktop) which contains both Docker and Docker-Compose tools.

Linux users need to follow the instructions on [Get Docker CE for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/) and then [Install Docker Compose](https://docs.docker.com/compose/install/) separately.

You are good to go when you can successfully run:

`docker-compose --version`

**ModHeaders**

To test our API, we use [Google Chrome](https://www.google.com/chrome/) with the [ModHeader](https://chrome.google.com/webstore/detail/modheader/idgpnmonknjnojddfkpgkljpfnnfcklj?hl=en) extension.

**Setup project**

Clone the project on GitHub.
```
git clone git@github.com:philippbruhin/recipe-app-api.git
```

Navigate into project folder (`cd recipe-app-api`) and run following command for building and docker image according the Dockerfile.
```
docker build .
```

Build docker image according docker compose file.
```
docker-compose build
```

Creating Django project from docker setup.
```
docker-composer run app sh -c "django-admin.py startproject app ."
```

Run tests with following command
```
docker-compose run --rm app sh -c "python manage.py test && flake8"
```

Make migrations of core app
```
docker-compose run app sh -c "python manage.py makemigrations core"
```

Creating a superuser for login into the /admin area
```
docker-compose run app sh -c "python manage.py createsuperuser"
```

Creating a new app called user (with removing docker container after running command)
```
docker-compose run --rm app sh -c "python manage.py startapp user"
```