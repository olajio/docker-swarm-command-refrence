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
