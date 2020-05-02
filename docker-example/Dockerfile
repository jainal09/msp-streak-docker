FROM python:3.8
# pulls official python image from docker hub
RUN apt-get update && rm -rf /var/lib/apt/lists/*
WORKDIR /usr/src/app
COPY requirements.txt ./
RUN pip install -r requirements.txt
COPY . .
EXPOSE 8000
# this exposes the containers port to be used inside by another container
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]