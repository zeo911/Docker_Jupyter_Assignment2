# Dockerfile for Jupyter Notebook

This Dockerfile sets up a Docker container to run a Jupyter Notebook server. The key steps are:

1. **Base Image**: We start from the `python:3.8` image, which includes Python 3.8 and is suitable for running Python applications.

2. **Working Directory**: We set `/app` as the working directory inside the container. All subsequent commands will be run from this directory.

3. **Copying Files**: We copy all files from the current directory on the host (`.`) into the `/app` directory inside the container. This includes the Jupyter notebooks and any other files you have in the directory.

4. **Exposing Port**: We expose port `8888`, which is the default port for Jupyter Notebook. This makes the Jupyter server accessible from outside the container.

5. **Command**: We specify the command to run the Jupyter Notebook server with the following options:
   - `--ip='0.0.0.0'`: This binds the server to all IP addresses of the container, making it accessible from any host.
   - `--port=8888`: This confirms the server runs on port `8888`.
   - `--no-browser`: This prevents Jupyter from trying to open a browser automatically.
   - `--allow-root`: This allows Jupyter to be run as the root user inside the container, which is necessary since Docker containers run as root by default.

By building a Docker image using this Dockerfile and running a container from it, you can easily start a Jupyter Notebook server that's ready for use.

# Running Jupyter Notebook in Docker

This guide will walk you through the process of building and running a Jupyter Notebook server in a Docker container using the provided Dockerfile.

## Building the Docker Image

First, you need to build your Docker image from the Dockerfile. Open your terminal and navigate to the directory containing your Dockerfile. Then run the following command:

```bash
docker build -t my-jupyter .
docker run -p 8888:8888 jupyter/datascience-notebook

