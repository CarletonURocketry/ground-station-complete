# CUInSpace Complete Ground Station Stack
The repository containing the complete CUInSpace ground station stack. The [ground-station](https://github.com/CarletonURocketry/ground-station) and [ground-station-ui](https://github.com/CarletonURocketry/ground-station-ui) repositories are located here as [git submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules), as well the directory containing the configuration and images for the [tile-server](https://github.com/CarletonURocketry/ground-station-complete/tree/main/tile-server) that makes use of [nginx](https://nginx.org/en/)

This repo can be used to easily deploy the full ground station using [Docker Compose](https://docs.docker.com/compose/). It can also be used end-to-end testing and development

## Setup
Because this repository uses git submodules, the setup is a little different than it is for regular repositories. In brief, the submodules in this repo are "pointers" to repositories elsewhere in the org and they must be initialized and populated in addition to being cloned. 

If you've haven't yet cloned the repository, you can use `git clone --recurse-submodules <url>` to automatically intialize and update the submodules. If you've already cloned the repository, you can use `git submodule init` and `git submodule update` or `git submodule update --init` to initialize and update the submodules. Finally, run `git submodule update --remote --merge` to fetch the latest changes to the main branch for each submodule. 

Note that because the tile images for the tile server are stored in this repo for convenience, this repo might take a few minutes to clone.

The setup steps for each repository can be found within their respective directories

## Deployment and Testing
The main advantage of this repository is being able to use [Docker Compose](https://docs.docker.com/compose/) to launch the entire ground station stack with a single command.

First, follow the installation guides for [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/). (Note: If you are using Windows, it is *highly* recommended that you also install [WSL2](https://learn.microsoft.com/en-us/windows/wsl/install))

To run the Python backend, React frontend and nginx tile server, use `docker compose up &`. If it is your first time running this command, it should take a few minutes to build the images, successive runs should execute much faster.

The frontend can be accessed at http://localhost:3000/ and the backend can be accessed at http://localhost:33845/. If you're really interested, the tiling server can be accessed at http://localhost:8000/ but you also can only query for the images directly.
