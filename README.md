# Quick-EK-Stack with TLS Enabled

Set up a Elastic Kibana stack with TLS enabled in a few minutes. Base taken from [elastic](https://github.com/elastic/stack-docs/tree/master/docs/en/getting-started/docker) and [this](https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-docker.html#get-started-docker-tls) tutorial.

Steps to follow:

1. Clone repository
2. Generate certificates

    ``` shell
    docker-compose -f create-certs.yml run --rm create_certs
    ```

3. Bring up elastic and kibana

    ``` shell
    docker-compose up -d
    ```

4. Generate Elastic passwords'

   - Automatic

    ```shell
    docker exec es01 /bin/bash -c "bin/elasticsearch-setup-passwords auto --batch --url https://es01:9200"
    ```

   - Interactive

    ```shell
    sudo docker exec -it es01 /bin/bash -c "bin/elasticsearch-setup-passwords interactive --url https://es01:9200"
    ```

5. Update new kibana_system password in `docker-compose.yml` and restart stack

Done!