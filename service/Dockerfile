############################
# Final container
############################
FROM registry.cto.ai/official_images/python:2-3.7-buster-slim

WORKDIR /ops

ADD requirements.txt .

RUN pip3 install -r requirements.txt

ENV IS_PIPELINE=False
# ENV DB_NAME='xyz'
# ENV DB_USER='xyz'
# ENV DB_PASSWORD='xyz'

ADD . .

# equivalent to make setup
# RUN python3 manage.py migrate

# the README asks for these steps but they aren't defined in the Makefile
# RUN python3 manage.py createsuperuser
# RUN python3 manage.py collectstatic

# equivalent to make lint
# RUN python3 -m flake8 --ignore E501,E722,F821,W504 apps/ project/ libs/

# equivalent to make tests
# RUN python3 manage.py test apps

# equivalent to make coverage
# RUN python3 manage.py test apps --with-coverage --cover-package=apps.user