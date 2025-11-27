**Running the Luxembourg Population REST Service in Docker** 

**Prerequisites**
Ensure that Docker is installed on your system before proceeding.

**1. Create the Docker Image**
bash
```bash 
docker build -t lupopulation-api .
```
This command will generate a Docker image "lupopulation-api"

**2. Start the Container**
Run the container with the following command:

```bash 
docker run -p 8000:8000 lupopulation-api
```
This will start the server, and the application will be accessible at `http://localhost:8000`.

**3. Check Running Containers**
To see all running containers:
```bash 
docker ps
```

**4. Stop a Container**
```bash 
docker stop <CONTAINER ID>
```

# How to Use the Service
The service is accessible via a single HTTP GET endpoint. 
- Directly in your browser – just enter the URL with the desired year
**`GET http://localhost:8080/api/population/2024`**
- Using curl in the command line
**`curl http://localhost:8000/api/population/2024`**
