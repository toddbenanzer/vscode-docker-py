# VSCode-Docker-Python

This is a template to get started with VSCode-Docker-Python.

## .devcontainer

This folder contains two files: `devcontainer.json` and `Dockerfile`. `devcontainer.json` has all the configuration controls for VSCode *inside* the Docker container. Any configuration you've made to your VSCode environment will not follow you inside the container. The `Dockerfile` here currently starts with a vanilla Python configuration. The key here is that the container will install the packages listed in `requirements.txt`.

## .vscode

`launch.json` is your typical VSCode launch configurations. I left this pretty vanilla. `settings.json` contains a few settings that I prefer, but these are by no means best practices.


## Executing in Linux

Here's a simple example of how I run any code that I create.

Create and enter a source code directory

`rm -rf /src`
`mkdir -p -m 777 /src`
`cd /src`

Retrieve the code from github.
`git init`
`git clone https://toddbenanze@github.com/toddbenanzer/vscode-docker-py.git`

Build the docker container. The command builds the docker container, applying the label and the tag 'vscodepy'.
`docker build --label vscodepy --tag vscodepy --file .devcontainer/Dockerfile /src`

Run the container. This runs the 'vscodepy' container in interactive mode, binding the /src directory as a volume mount. Inside the container, the `python /src/main.py` command is executed.
`docker run --interactive --volume /src:/src vscodepy python /src/main.py`
