# docker-gpu

## Installation

1. Install docker ([https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/))

1. Add nvidia runtime ([https://stackoverflow.com/questions/59008295/add-nvidia-runtime-to-docker-runtimes](https://stackoverflow.com/questions/59008295/add-nvidia-runtime-to-docker-runtimes))

## How to use?

1. pull image from dockerhub
    ```bash
    docker pull chanok203/ml:cuda11.8.0-py311
    ```

1. create docker-compose.yml

    ```yml
    version: "2.4"

    services:
        jupyter:
            image: chanok203/ml:cuda11.8.0-py311
            runtime: nvidia
            environment:
            - NVIDIA_VISIBLE_DEVICES=0,1
            restart: unless-stopped
            ports:
            - 80:8888
            volumes:
            - /home/<USER>/volume:/notebooks/volume
    ```

2. run this command

    ```bash
    docker compose up
    ```

## Authors

1. Chanok Pathompatai (cpathompatai@gmail.com)