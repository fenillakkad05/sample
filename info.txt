
docker --version

mkdir Docker_IT077
cd Docker_IT077

notepad reg.html
notepad Dockerfile

docker build -t my-img:v1 .
docker images

docker run -d -p 8083:80 --name my-cont my-img:v1
docker ps ( check running containers )
docker ps -a ( check all containers )

docker stop my-cont
docker start my-cont
docker stop my-cont
docker rm my-cont

docker login  ( login na hoy to docker login fenillakkad)
docker tag my-img:v1 fenillakkad/my-img:v1
docker push fenillakkad/my-img:v1

# Run these on another computer:
docker pull kirtan107/my-img:v1
docker run -d -p 8083:80 --name my-cont kirtan107/my-img:v1



reg.html
=> 
<!DOCTYPE html>
<html>
<head>
    <title>Registration Page</title>
</head>
<body>
    <h1>Student Registration</h1>

    <form>
        <label>Name:</label>
        <input type="text" name="name">
        <br><br>

        <label>Email:</label>
        <input type="email" name="email">
        <br><br>

        <label>Password:</label>
        <input type="password" name="password">
        <br><br>

        <button type="submit">Register</button>
    </form>
</body>
</html>


Dockerfile
=> 
FROM nginx:alpine
COPY reg.html /usr/share/nginx/html/index.html
EXPOSE 80



-------------------------------------------------------- java
docker build -t java-img:v1 .
docker run --name java-cont java-img:v1

Dockerfile
=> FROM eclipse-temurin:21-jdk-alpine
WORKDIR /app
COPY Main.java .
RUN javac Main.java
CMD ["java", "Main"]

Main.java 
=> 
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello from Java Docker!");
        System.out.println("IT077 - Docker Practical");
    }
}


----------------------------------------------------------- python

docker build -t python-img:v1 .
docker run --name python-cont python-img:v1

Main.py
=> 
print("Hello from Python Docker!")
print("IT077 - Docker Practical")

Dockerfile
=> 
FROM python:3.12-alpine

WORKDIR /app

COPY main.py .

CMD ["python", "main.py"]


---------------------------------------------

docker pull kirtan107/java-img:v1
docker run --name java-cont kirtan107/java-img:v1
