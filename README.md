# learning-langchain

## Local setup

Prerequisites:
- python 3.13

### install dependencies
```python
python -m pip --install upgrade pip
python -m pip install pipenv

# install dependencies and create virtual environment
python -m pipenv sync

# add virtual env python binary to jupyter list of kernels
python -m pipenv shell

# when inside the shell
python -m ipykernel install --user --name=learning-langchain 

# start jupyter
jupyter lab # or python -m jupyter lab
```

## Running a pgvector instance using docker
### Prerequisite
- Docker installation.  

### Create a volume
You will need to create a volume if you want to persist your data
```shell
docker volume create pgvector-data
```

### create and run docker container
```shell
docker container run --read-only \ # ensure that all data goes to volume
 --name pgvector-container -e POSTGRES_USER=langchain -e POSTGRES_PASSWORD=langchain -e POSTGRES_DB=langchain \ # set credentials
 -p 6024:5432 \ # configure port
 -d --mount type=volume,src=pgvector-data,dst=/var/run/postgresql \ # mount created volume to data path on container
 pgvector/pgvector:pg16
```
### stop/start container
the command above should be run once (first time)
for subsequent runs, use these commands
```
docker stop pgvector-instance 
docker start pgvector-instance
```
