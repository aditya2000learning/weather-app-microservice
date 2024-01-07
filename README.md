# weather-app-microservice

## Steps:


# db:
- docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=aditya mysql

# auth:
- cd auth
- docker build -t auth:v1.0.0 .
- docker run -d -p 8080:8080 -e DB_HOST=172.17.0.1 -e DB_PASSWORD=aditya auth:v1.0.0
- curl -XPOST -d '{"user_name":"user1","user_password":"mypass"}' localhost:8080/users
- curl -XPOST -d '{"user_name":"user1","user_password":"mypass"}' localhost:8080/users/user1

# Weather:
- cd weather
- docker build -t weather:v1.0.0 .
- docker run -d -p 5000:5000 -e APIKEY=ecbc396f46mshb65cbb1f82cf334p1fcc87jsna5e962a3c542 weather:v1.0.0

# UI:
- cd UI 
- docker build -t ui:v1.0.0 .
- docker run -d -p 3000:3000 -e AUTH_HOST=172.17.0.1 -e AUTH_PORT=8080 -e WEATHER_HOST=172.17.0.1 -e WEATHER_PORT=5000 ui:v1.0.0
