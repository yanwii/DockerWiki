# DockerWiki


## 1.REGISTRY

#### CREATE REGISTRY
    docker pull registry
    docker run -d -v /opt/registry:/var/lib/registry -p 5000:5000 --restart=always registry

#### CHECK REPOSITORY
    curl http://your_ip:your_port/v2/_catalog

#### CHECK TAG LIST
    curl http://your_ip:your_port/v2/your_image/tags/list

#### PUSH IMAGES
    > docker images
    REPOSITORY                          TAG                 IMAGE ID            CREATED             SIZE
    ubuntu                              15.10               9b9cb95443b5        2 years ago         137MB

    > docker tag 9b9cb95443b5 your_ip:your_port/ubuntu:your_tag
    > docker images
    REPOSITORY                          TAG                 IMAGE ID            CREATED             SIZE
    your_ip:your_port/ubuntu            15.10               9b9cb95443b5        2 years ago         137MB
    ubuntu                              15.10               9b9cb95443b5        2 years ago         137MB

    > docker push your_ip:your_port/ubuntu
    > curl http://your_ip:your_port/v2/_catalog
    {
        "repositories": [
            "ubuntu"
        ]
    }
    > cur http://your_ip:your_port/v2/ubuntu/tags/list
    {
        "name": "ubuntu",
        "tags": [
            "15.10"
        ]
    }


## 2.IMAGE

#### LIST IMAGE
    > docker images

#### PULL IMAGE
    > docker pull your_ip:your_port/ubuntu:your_tag

#### RUN IMAGE
    > docker run --name image_name your_ip:your_port/ubuntu:your_tag

#### REMOVE IMAGE
    > docker image rm image_name


## 3.CONTAINER

#### START CONTAINER
    > docker start container_name
    > docker container start container_name

#### STOP CONTAINER
    > docker stop container_name
    > docker container stop container_name
