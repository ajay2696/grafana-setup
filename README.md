# Grafana Setup

This project contains configuration files to build and deploy Grafana using Docker Desktop.

## Prerequisites

- Docker Desktop installed and running on macOS or Windows.

## Setup Instructions

1. **Clone the Repository**:
    ```sh
    git clone <repository-url>
    cd <repository-directory>
    ```

2. **Create Docker Compose File**:
   Ensure the `docker-compose.yml` file is present in the project directory with the following content:
    ```yaml
    version: '3.1'

    services:
      grafana:
        image: grafana/grafana:latest
        container_name: grafana
        ports:
          - "3000:3000"
        volumes:
          - grafana-storage:/var/lib/grafana
        environment:
          - GF_SECURITY_ADMIN_PASSWORD=admin

    volumes:
      grafana-storage:
    ```

3. **Start Grafana**:
   Open a terminal, navigate to your project directory, and run the following command to start Grafana:
    ```sh
    docker-compose up -d
    ```

4. **Access Grafana**:
   Open your web browser and go to `http://localhost:3000`. Log in with the default credentials:
    - Username: `admin`
    - Password: `admin`

5. **Configure Grafana**:
   Once logged in, you can start configuring Grafana by adding data sources, creating dashboards, and setting up alerts.

## Project Structure

- `docker-compose.yml`: Docker Compose configuration file for Grafana.
- `README.md`: Project documentation.

## License

This project is licensed under the MIT License.