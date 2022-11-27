# A Python Jupyter Example Notebook in Dev Containers

## Introduction

GitHub.com offers a way to deploy an application in Docker Container on the Microsoft Azure Cloud.
This example app illustrates how to do that by deploying a Python Jupyter Example Notebook.

## GitHub DevContainer with GitHub Codespaces

GitHub Codespaces is the service to create a container development environment on the Microsoft Azure Cloud.
To do so one need to define the environment with a file `devcontainer.json` in folder `.devcontainer`.

## Dev Container Definition File

This the definition file for the Dev Containers.
Please read the [Dev Container documentation](https://containers.dev/implementors/json_reference/) to know more about the keywords involved.

```
{
  "name": "Python Jupyter Example Notebook in DevContainer",
  "dockerComposeFile": "../docker-compose.yml",
  "service": "jupyter-minimal",
  "workspaceFolder": "/workspaces/${localWorkspaceFolderBasename}",

  "extensions": [
    "ms-python.python",
    "ms-toolsai.jupyter",
    "ms-toolsai.jupyter-keymap",
    "ms-toolsai.jupyter-renderers"
  ],

  "forwardPorts": [8888],
  
  "postCreateCommand": "jupyter notebook"
}
```

### Keyword `name`

A name for the Dev Container.

### Keyword `dockerComposeFile`

You can specify a Docker Compose file to be executed to spin up the containers.

### Keyword `service`

Specify a container to conect to once the app is running when a Docker Compose file is given.

### Keyword `workspaceFolder`

Set the path to open in when connecting to the container.

### Keyword `extensions`

Defines which extensions to load into the Dev Container.
Here we use the Python and Jupyter extensions.

### Keyword `forwardPorts`

An array of port numbers that should be forwarded from inside the primary container to the local machine.
Here we expose the ports 8888 for the Python Jupyter Notebook.

### Keyword `postCreateCommand`

A command to be executed once the Dev Containers are created.
Please note that it is not enough to define an ENTRYPOINT for a container in the Dockerfile.
Here we start the Python Jupyter Notebook.

## Run Dev Container

Go to the GitHub.com project, click on thhe "Code" button, choose the "Codespaces" tab, click "Create codespace on main" button.
Wait until all is created and a web Visual Studio Code IDE version is launched.
Click on the "ports" tab and open URL for port 8888 in a browser.
Enjoy the Python Jupyter Example Notebook.
