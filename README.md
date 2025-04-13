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
