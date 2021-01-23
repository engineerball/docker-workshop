# Docker Workshop
Lab 01: First interactions with containers

---

## Preparations (before a demo)

 - Pull the jenkins image:

```
$ docker pull tshaiman/jenkins-blueocean
```

## Instructions

 - Check the current running containers and images:
```
$ docker ps
```
```
$ docker images
```

 - Browse to the port 8080 to show to show that it's empty:
```
http://localhost:8080
```

 - Run a Jenkins container
```
$ docker run --name jenkins -p 8080:8080 tshaiman/jenkins-blueocean
```

 - Browse to the Jenkins application
```
http://localhost:8080
```

 - Search for the administrator password in the log:
```
*************************************************************
*************************************************************
*************************************************************  
Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:  
f7702d8c3e204cf7bfcce76dea9e1ec0  
This may also be found at: /var/jenkins_home/secrets/initialAdminPassword  
*************************************************************
*************************************************************
*************************************************************
```

 - Configure Jenkins using the administration password
 
 ## Task
 You will run Redis On Port 6379 , connect to it from Both CLI and from GUI Tool

1. Download , configure and run Free Redis UI Tool: https://redislabs.com/blog/redisinsight-gui/

2. Create a Redis Container running on port 6379, use your own name instead "some-redis"


```
$ docker run --name some-redis -d -p 6379:6379 redis
```


3. Create a Second Redis Container Instance running the command redis-cli and connecting it to the first container.
use your own name for the CLI container and don't forget to connect it to the first container name

```
$ docker run -it --name my-redis-cli --link some-redis:redis --rm redis redis-cli -h some-redis -p 6379
```

4. when the CLI container starts , add a key to it using Redis CLI 

```
$ Set "my-val" 14
```

5. Open redisInsight UI , add your connection details ( localhost ,port 6379  , and look for the key you have added )


## CleanUp

```
$ docker rm -f $(docker ps -a -q)
```

