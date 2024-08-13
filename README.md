Here's a template for a README file for a project that involves containerizing a sample Node.js application:

---

# Containerizing a Sample Node.js Application

## Project Overview

This project demonstrates how to containerize a simple Node.js application using Docker. Containerization allows the application to be packaged with all its dependencies, ensuring consistent behavior across different environments.

## Table of Contents

- [Project Overview](#project-overview)
- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [Setup Instructions](#setup-instructions)
- [Running the Application](#running-the-application)
- [Docker Commands](#docker-commands)
- [Customization](#customization)
- [Contributing](#contributing)
- [License](#license)

## Prerequisites

Before starting, ensure you have the following installed on your machine:

- [Node.js](https://nodejs.org/) (v14.x or later)
- [Docker](https://www.docker.com/) (v20.x or later)

## Project Structure

```bash
.
├── node_modules/       
│   ├── Rest files
├── spec/       
│   ├── Rest files
├── src/
│   ├── index.js        # Node.js index file
│   ├── Rest files
├── .gitignore
├── Dockerfile          # Dockerfile for building the Node.js app image
├── package.json        # Node.js project metadata and dependencies
├── package-lock.json
└── README.md           # Project documentation
```

### `index.js`

A simple Node.js application that listens on port 3000 and returns a simple notes applictaion when accessed.

## Setup Instructions

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Riyanshj/Containerizing-A-Sample-Node.js-Application.git
   cd Containerizing-A-Sample-Node.js-Application
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

## Running the Application

### Running Locally

To run the application locally without Docker:

1. **Start the application**:
   ```bash
   node index.js
   ```

2. **Access the application**:
   Open your browser and navigate to `http://localhost:3000`.


### Creating the Dockerfile

1. **Create a Docker File**:
   Name the file Docker #Make sure the name is Dockerfile

2. **Build the Docker File**:
   ```bash
    # Using official node.js runtime as a image
    FROM node:21-alpine

    # Setting working directory
    WORKDIR /usr/src/app

    # Copying project.json and projecy-lock.json to the working directory
    COPY package*.json ./

    # Using run command to install dependencies
    RUN npm install

    # Copy rest application code
    COPY . .

    # Exposing thr port 
    EXPOSE 3000

    # Command to run Node.js application
    CMD ["npm" , "start"]
   ```

### Running with Docker

1. **Build the Docker image**:
   ```bash
   docker build -t sample-nodejs-app .
   ```

2. **Run the Docker container**:
   ```bash
   docker run -p 3000:3000 sample-nodejs-app
   ```

3. **Access the application**:
   Open your browser and navigate to `http://localhost:3000`.

## Docker Commands

- **Build the Docker image**:
  ```bash
  docker build -t sample-nodejs-app .
  ```

- **Run the Docker container**:
  ```bash
  docker run -p 3000:3000 sample-nodejs-app
  ```

- **Stop the Docker container**:
  ```bash
  docker stop <container_id>
  ```

- **Remove the Docker container**:
  ```bash
  docker rm <container_id>
  ```

- **Remove the Docker image**:
  ```bash
  docker rmi sample-nodejs-app
  ```

## Customization

- **Change the listening port**: Modify the port number in `index.js` and update the Docker `-p` flag accordingly.
- **Add environment variables**: Update the `Dockerfile` to pass environment variables during build or runtime.

## Contributing

If you want to contribute to this project, feel free to submit a pull request or open an issue.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
