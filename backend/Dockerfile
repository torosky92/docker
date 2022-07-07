FROM python:3.7.4-alpine3.10

LABEL maintainer="David Antonio Toro Medina <david-toro92@hotmail.com>"
RUN pip install --upgrade pip
RUN apk update
RUN apk upgrade
RUN apk add --no-cache bash git openssh vim 
RUN apk add --no-cache python3-dev libstdc++ 
RUN apk add --no-cache g++
RUN apk add --no-cache postgresql-dev gcc python3-dev musl-dev 
RUN ln -s /usr/include/locale.h /usr/include/xlocale.h
RUN apk del --purge gcc musl-dev libffi-dev openssl-dev
RUN apk add gcc musl-dev python3-dev libffi-dev openssl-dev cargo 
RUN pip install cryptography==3.3.2
RUN pip install flask-talisman==0.8.1
RUN apk del --purge gcc musl-dev libffi-dev openssl-dev
ARG SSH_PRIVATE_KEY
WORKDIR /server/production
RUN git config --global user.name "torosky92" && git config --global user.email "david-toro92@hotmail.com"
ADD ./build/backend/requirements.txt /server/backend/requirements.txt
WORKDIR /server/backend
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

