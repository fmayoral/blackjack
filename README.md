# Blackjack Docker Compose Setup

This repository orchestrates the deployment of the Blackjack game using Docker Compose, including a React-based frontend service, a Spring Boot backend service, and MongoDB as the database.

## Prerequisites

Before you start, make sure you have the following installed on your system:
- Git
- Docker
- Docker Compose

## Cloning the Repository

To include the frontend and backend services as submodules, clone this repository with the `--recurse-submodules` flag:

```bash
git clone --recurse-submodules https://github.com/fmayoral/blackjack.git
```

If you've already cloned the repository without submodules, you can initialize and update them with:

```bash
cd blackjack
git submodule update --init --recursive
```

## Configuring environmental variables
Included in the project there's a `.env.template` file.

You need to copy this file and rename it to `.env`.

Now in your new `.env` file you should replace the values for your own local environment values.

## Running the Services with Docker Compose

Navigate to the root directory of the cloned repository:

```bash
cd blackjack
```

Build and start the services using Docker Compose:

```bash
docker-compose up --build
```

This command does the following:
- Builds the Docker images for the frontend and backend services if they don't exist.
- Starts the MongoDB, backend, and frontend services in containers.
- Starts a HyperDx local server for application monitoring.
- Maps the necessary ports to your host, making the services accessible via your web browser.

## Accessing the Application

Once all services are up and running:
- The frontend service will be available at [http://localhost:3000](http://localhost:3000).
- The backend API can be accessed at [http://localhost:8080](http://localhost:8080).
- The Keycloak blackjack realm admin can be accessed at [http://localhost:9090](http://localhost:9090/admin/master/console/#/BlackjackRealm/realm-settings).
- The HyperDX Local server for monitoring can be accessed at [http://localhost:9000](http://localhost:9000).

## Stopping the Services

To stop the running containers and remove them, use the following command in the terminal where Docker Compose is running:

```bash
docker-compose down
```

## Updating Submodules

If there are updates to the frontend or backend services and you want to pull the latest changes, run:

```bash
git submodule update --remote
```

Then, rebuild and restart the services with Docker Compose:

```bash
docker-compose up --build
```

## Additional Information

- **Submodules**: This project uses Git submodules to include the frontend and backend services. This allows for independent development of these services while easily combining them for deployment.
- **Environment Variables**: The project uses environment variables (e.g., `SPRING_PROFILES_ACTIVE`, `MONGO_URI`) to configure the backend service. These are set in the `docker-compose.yml` file and can be modified as needed.
