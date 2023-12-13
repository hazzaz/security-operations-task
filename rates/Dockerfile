# syntax=docker/dockerfile:1

FROM python:3.8-slim-buster
ENV FLASK_APP wsgi.py
WORKDIR /python-docker

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

EXPOSE 3000

#CMD [ "python3", "-m" , "flask", "run"]
CMD ["gunicorn"  , "-b", "0.0.0.0:3000", "app:app"]