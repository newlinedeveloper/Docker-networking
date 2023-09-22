# Docker-networking
Docker Networking Basics and Advanced topics
Certainly, here are some commands and samples you can include in the blog to help readers implement Docker networking:

**Docker Bridge Networking**

- **Create a Custom Bridge Network:**

    ```bash
    docker network create my-bridge-network
    ```

- **Run a Container on a Custom Bridge Network:**

    ```bash
    docker run -d --name my-container --network my-bridge-network nginx
    ```

**Docker Host Networking**

- **Run a Container Using Host Networking:**

    ```bash
    docker run -d --name my-container --network host nginx
    ```

**Docker Overlay Networking**

- **Create an Overlay Network:**

    ```bash
    docker network create -d overlay my-overlay-network
    ```

- **Deploy a Service on the Overlay Network (Docker Swarm):**

    ```bash
    docker service create --name my-service --network my-overlay-network nginx
    ```

**Docker Macvlan Networking**

- **Create a Macvlan Network:**

    ```bash
    docker network create -d macvlan --subnet=192.168.1.0/24 --gateway=192.168.1.1 -o parent=eth0 my-macvlan-network
    ```

- **Run a Container on a Macvlan Network:**

    ```bash
    docker run -d --name my-container --network my-macvlan-network nginx
    ```

**Advanced Docker Networking**

- **Leverage Docker Compose for Multi-Container Setup:**

    Create a `docker-compose.yml` file:

    ```yaml
    version: '3'
    services:
      web:
        image: nginx
        networks:
          - my-custom-network

    networks:
      my-custom-network:
        driver: bridge
    ```

    Run the Docker Compose stack:

    ```bash
    docker-compose up -d
    ```

**Docker Networking Tools**

- **List Docker Networks:**

    ```bash
    docker network ls
    ```

- **Inspect a Docker Network:**

    ```bash
    docker network inspect my-network
    ```

**Troubleshooting Docker Networking**

- **Check Container Network Connectivity:**

    ```bash
    docker exec -it my-container ping google.com
    ```

- **View Container Network Traffic:**

    ```bash
    docker exec -it my-container tcpdump -i eth0
    ```

**Security Best Practices**

- **Limit Container Access to Host Resources:**

    When running a container, use the `--cap-drop` and `--cap-add` options to restrict or grant specific Linux capabilities:

    ```bash
    docker run --cap-drop=all --cap-add=NET_RAW -d nginx
    ```

- **Segment and Isolate Networks:**

    Utilize Docker's built-in network segmentation to isolate services from each other. Design your network topologies to minimize exposure.
