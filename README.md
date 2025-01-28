# Installing Matirx instance (synapse)
 *With docker*

## Install all the packages

```bash
sudo apt update
sudo apt install -y docker.io docker-compose
```

## Create a directory for synapse

```bash
mkdir synapse && cd synapse 
```

## Inside the synapse folder, run the docker :
```bash
docker-compose up -d
```
The synapse server should be running on localhost

## In case of issues :

### Check docker's logs :
```bash
docker logs synapse
```
### Regenerate the config file :
```bash
#Shut down the docker :

docker-compose down

#Generate the config file :

docker run -it --rm \
    -v $(pwd)/data:/data \
    -e SYNAPSE_SERVER_NAME=localhost \
    -e SYNAPSE_REPORT_STATS=no \
    matrixdotorg/synapse:latest generate

#Restart the docker :

docker-compose up -d
```

## Register an user :
```bash
docker exec -it synapse register_new_matrix_user -c /data/homeserver.yaml http://localhost:8008
```
And then follow instructions on the console


## Check status :
Open your browser at ``http://localhost:8008``

And then download a matrix client like Element to use your brand new Matrix server



