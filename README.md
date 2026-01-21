# Requirements
1. Use terraform to create an ECS cluster (one task definition, 2 tasks)
2. Dockerize the hello world flask app
3. Deploy the hello world flask app in the cluster
4. Create a CI/CD of the hello world flask app such that: 
  a. On PR, test the app, and not allow a merge if it fails
  b. On Merge, the app should re-deploy

# Overview 
## First step
* Run `setup.sh` to clone the terraform [melford2-iac](https://github.com/fptiangco/melford2-iac) and flask app [melford2-api](https://github.com/fptiangco/melford2-api) repos here.

## Folder structure
* The stack is made up of 3 repos, this first repo (melford2) serves as a parent directory for the 2 other repos: the terraform (melford2-iac) and flask app (melford2-api) repos.
* Separating the terraform (melford2-iac) and flask app (melford2-api) repos mimics an environment where different teams work in their specific areas. The top-level repo (melford2) provides features such as docker compose or devcontainers.



## 2 options for Running / Developing the app

### 1. Via devcontainers
* Via vscode and the devcontainer extension
* Choose `Dev Containers: Rebuild and Reopen in Container` and choose either the `API Dev Container` or the `Terraform  Dev Container`


### 2. Via docker compose
#### Just Run the App
* not for development, directories are not mounted, this just runs flask app
```
docker compose -f docker-compose-build.yml build
docker compose -f docker-compose-build.yml up
```
* then localhost:5000

#### For Development
* for development of both the flask and terraform repos, directories are mounted
```
docker compose -f docker-compose-dev.yml build
docker compose -f docker-compose-dev.yml up
```
* then exec into container to create the venv and run the app manually



