docker

docker build -t c-port-listener .
docker run  -d -p 8080:8080 --name port_listener c-port-listener


curl -d "Hello from curl!" http://localhost:8080
echo "Test message" | nc localhost 8080
cat /home/alexeigu/test/docker/logs/received_messages.log

docker logs port_listener

docker build -t <image name> . — create a image
docker images — check the images
docker run -d <immage name> — run docker image
docker logs -f abcd1234efgh — to see the logs

docker ps # List running containers
docker ps -a # List all containers (including stopped)

docker rmi <image_name> # Remove an image

docker stop <container_id> # Stop a running container
docker start <container_id> # Start a stopped container

