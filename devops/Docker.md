Update docker images.

	docker-compose pull
	docker-compose up --force-recreate --build -d
	docker image prune -f
docker-compose down && docker-compose build --pull && docker-compose up -d

 Building a dockerfile [Build Container](https://learn.microsoft.com/en-us/dotnet/core/docker/build-container?tabs=linux&pivots=dotnet-8-0)


- Docker run command examples:

- With interactive terminal:
- docker run -d --name=guacamole \
    
    -p 8348:8080 \  
    -e PUID=1026 \  
    -e PGID=100 \  
    -e TZ=Europe/Bucharest \  
    -v /volume1/docker/guacamole:/config \  
    --restart always \  
    jwetzell/guacamole  
    

- You need to tag your image correctly first with your `registryhost`:
-   docker tag [OPTIONS] IMAGE[:TAG] [REGISTRYHOST/][USERNAME/]NAME[:TAG]
    
- Then docker push using that same tag.
-   docker push NAME[:TAG]
    
- Example:
-   docker tag 518a41981a6a myRegistry.com/myImage
      docker push myRegistry.com/myImage