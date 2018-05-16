# Docker-and-WebServices

## Command to Run My Docker

Pull the image from my DockerHub
```
docker pull dellvo/siqi_app
```
Rum the image
```
docker run -d --name weather -p 8081:80 -t dellvo/siqi_app
```

## URLs to Previous Homeworks

### Homework 2 -- Weather API
All available data:

http://0.0.0.0:8081/api/historical

Data from a particular date:

http://0.0.0.0:8081/api/historical/20170101

### Homework 3 -- Weather UI

http://0.0.0.0:8081



## Steps to Port the WebSerice to Docker

The project should have the following directory structure.

```
My_App/

  Dockerfile
  
  requirements.txt
  
  app/
    main.py
    
    /templates
      index.html
    
    /static
      style.css
      main.js
      jquery.js
      
      /images
```


### Docker Build

```
docker build -t siqi_app .
```

### Docker Run

```
docker run -d --name weather1 -p 8081:80 -t siqi_app
```

* `-d` runs the Docker container as a daemon in the background.
* `-p` connects port 80 of the Docker container to port 80 of your machine, so HTTP can work.
* `-t` specifies the tag of the container we want to run.
* `--restart=always` can be added so that it restarts the container if it crashes, or if the system docker is running on is rebooted.

If you get an error like “address already in use” or “port 80 already in use”:
* Make sure your Flask app or another app isn’t already running and using port 80
* Sometimes docker doesn’t unbind ports after you close containers, so try sudo service docker restart then run your container again.

We can see what Docker containers are actively running with `docker ps`.
If we want to kill the container, use `docker kill <container name>`.

### Push Image to DockerHub

```
docker tag siqi_app dellvo/siqi_app
docker push dellvo/siqi_app
```



## References:

uwsgi-nginx-flask
https://hub.docker.com/r/tiangolo/uwsgi-nginx-flask/

https://ianlondon.github.io/blog/deploy-flask-docker-nginx/

https://medium.com/@charlie.b.ohara/building-a-flask-rest-api-with-docker-94ca4219f460
