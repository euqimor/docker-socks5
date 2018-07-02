# docker-socks5
Docker container for socks5 proxy
* based on https://github.com/wernight/docker-dante
* updated to use alpine3.7, dumb-init1.2.1
* supports user creation on docker build

## Usage

#### Build:
Use the command below to build the image, replace `username` and `password` with desired values.
```
docker build -t dante-socks5 . --build-arg SOCKET_USER=username --build-arg SOCKET_PASSWORD=password --no-cache --force-rm
```
#### Run:
Run the compiled image with the following command. Replace `9889` with the desired external port number and `dante-socks5` with your compiled image name if it differs.
```
docker run -d -p 9889:1080 --restart unless-stopped dante-socks5
```
#### Manage:
When your container is running you can manage users and their passwords. In the following commands replace `username` with the actual username you want to manage, and `your_container` - with the name of the running container (can be seen in `docker container ls`)

- Create a new user:
```
docker exec -it your_container adduser username
```
- Delete a user:
```
docker exec -d your_container deluser username
```
- Change a user's password:
```
docker exec -it your_container passwd username
```
