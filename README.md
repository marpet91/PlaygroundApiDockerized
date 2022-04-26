# PlaygroundApiDockerized

## Build Docker Image

From project root, call the following command:

    docker build -f src\Playground.API\Dockerfile -t testapi

## Run Docker Image

Call from CLI:

    docker run -d -p 8080:80 testapi
	
After that, the weahter forecast will be shown when calling localhost:8080/weahterforecast
