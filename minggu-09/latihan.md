#### Clone the Lab’s GitHub Repo
``` git clone https://github.com/dockersamples/linux_tweet_app```

### Task 1: Run some simple Docker containers
#### Run a single task in an Alpine Linux container
1. Run the following command in your Linux console.
``` docker container run alpine hostname```
2. Docker keeps a container running as long as the process it started inside the container is still running. 
```  docker container ls --all```
#### Run an interactive Ubuntu container