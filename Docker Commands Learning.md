#### a. Docker Run and Stop Commands
	1. to start the container
		 $ docker start container_name
	2. to stop the contianer
		$ docker stop container_name # via container_name
		$ docker stop container_id   # via container_id
	 3. to see the stats
		 $ docker stats container_name

#### b. Docker Pull Image and Run
	1. pull the image
		$ docker pull centos  # here centos is the image name
	2. run the container: 
		a. via specifying container and image name
			$ docker run -d -t -name  container_name image_name  
		b. via specifying container id - provides container id
			$ docker run -d image_name 
		c. default run without any container specified
			$ docker run image_name
#### c. Docker Container and Image List

	1. to see the running containers
		$ docker ps 
	2. to see the running images
		$ docker images