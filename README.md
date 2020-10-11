# docker-swarm-command-refrence
Docker swarm command refrence

## docker swarm

### Description
#### Manage Swarm

API 1.24+  The client and daemon API must both be at least 1.24 to use this command. Use the docker version command on the client to check your client and daemon API versions.

Swarm This command works with the Swarm orchestrator.

### Usage
- `docker swarm COMMAND`

### Extended description

Manage the swarm.

### Parent command
| Command       | Description                          | 
| ------------- |:------------------------------------:| 
| docker        | The base command for the Docker CLI. | 

### Child commands
| Command       | Description                          | 
| ------------- |:------------------------------------:| 
| docker swarm ca | Display and rotate the root CA | 
| docker swarm init      | Initialize a swarm      | 
| docker swarm join | 	Join a swarm as a node and/or manager    | 
| docker swarm join-token | Manage join tokens | 
| docker swarm leave    | Leave the swarm      | 
| docker swarm unlock	| Unlock swarm |
| docker swarm unlock-key |	Manage the unlock key |
| docker swarm update | Update the swarm |

Please see [official docker swarm reference](https://docs.docker.com/engine/reference/commandline/swarm/) for the updated and latest docker swarm reference


# Creating a Docker Swarm Cluster from scratch

Note: Docker Swarm comes pre-installed with docker. That's quite unlike Docker Compose

1. Obtain the public IP of the master

2. On the master, type the command `docker swarm init --advertise-addr=x.x.x.x`
    - Note: 
      - `x.x.x.x` is IP address of the master
      - Whichever host on which the above command is run becomes the master

3. Once you run the above command, you'll get an output that looks like the following:

```
Swarm initialized: current node (sdeypqrji66yks2bo13sxabcd) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-2kqwu0gt7tg9btl9xxbm2oiwtvceg7gexlpq99gn33herac84k-c2zurwi6wa2n2e1y42esl2691 47.220.99.154:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
```

4. Keep the command `docker swarm join --token SWMTKN-1-2kqwu0gt7tg9btl9xxbm2oiwtvceg7gexlpq99gn33herac84k-c2zurwi6wa2n2e1y42esl2691 47.220.99.154:2377` handy so you can run it on any host you want to join to the docker swarm. Note that: docker must have been installed on the node you want to join to the swarm before running this command


5. Optional: You can run the command `docker node ls` to list the nodes in the docker swarm


# Launch Application into docker Swarm

## Creating a service in Docker Swarm.

Note: Any application you deploy in Docker Swarm is called a **Service**. A service is an abstraction of the containers underlying it. In other words, the service is the endpoint through which the underlying containers is reached. See [How services work](https://docs.docker.com/engine/swarm/how-swarm-mode-works/services/) for more information on Docker Swarm Services

1. To create a service you would run the `docker service create` command. The syntax for the command is: `docker service create --name <name-of-service> --replicas <number_of_replicas> <image-name>`. For example: `docker service create --name redis redis:3.0.6`

2. To create a service with a number of replicas, say 5 replicas, you run the command as follows: `docker service create --name redis --replicas=5 redis:3.0.6`

Another example showing port mapping: docker service create --name nginx --replicas 3 -p 80:80 nginx

3. Once the service is created, the underlying containers would be automatically distributed to the nodes in the docker swarm

4. Once the service is created, try accessing the service from the Master IP as well as the IPs of the Slaves

See [docker service CLI reference](https://docs.docker.com/engine/reference/commandline/service/) for more details on docker commands to manage your docker service
