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

## Grafana Dashboard Setup

1. **Add Prometheus Data Source**:
   - Go to **Configuration** > **Data Sources**.
   - Click **Add data source**.
   - Select **Prometheus**.
   - Set the URL to your Prometheus server (e.g., `http://localhost:9090`).
   - Click **Save & Test** to verify the connection.

2. **Create a Dashboard**:
   - Go to **Create** > **Dashboard**.
   - Click **Add new panel**.

3. **Example Panels**:

   - **CPU Usage Panel**:
      - In the **Query** section, select **Prometheus** as the data source.
      - Enter the query: `rate(node_cpu_seconds_total{mode="idle"}[5m])`
      - Set the visualization type to **Graph**.
      - Configure the panel title to "CPU Usage".
      - Click **Apply** to save the panel.

   - **Memory Usage Panel**:
      - In the **Query** section, select **Prometheus** as the data source.
      - Enter the query: `node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes * 100`
      - Set the visualization type to **Gauge**.
      - Configure the panel title to "Memory Usage".
      - Click **Apply** to save the panel.

   - **HTTP Requests Panel**:
      - In the **Query** section, select **Prometheus** as the data source.
      - Enter the query: `rate(http_requests_total[5m])`
      - Set the visualization type to **Bar Gauge**.
      - Configure the panel title to "HTTP Requests".
      - Click **Apply** to save the panel.

4. **Save the Dashboard**:
   - Click the **Save** icon at the top of the dashboard.
   - Enter a name for your dashboard and click **Save**.

These steps will help you set up example panels for CPU usage, memory usage, and HTTP requests in your Grafana dashboard.

## Project Structure

- `docker-compose.yml`: Docker Compose configuration file for Grafana.
- `README.md`: Project documentation.




## License

This project is licensed under the MIT License.