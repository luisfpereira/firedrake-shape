# Installation

```bash
cd install

# bring dependencies in
git clone https://github.com/luisfpereira/FInAT/
git clone https://github.com/luisfpereira/ufl/
git clone https://github.com/luisfpereira/tsfc/

# create docker image
docker build -t firedrake-shape .
```

One of the docker images has a jupyter notebook entry point. To install it:

```bash
docker build -t shape-notebook dockerfile.jupyter
```

# Usage

To launch docker and work with jupyter notebooks:

```bash

mkdir notebooks
cd notebooks

docker run --rm -i -t -p 8888:8888 --mount src="$(pwd)",target=/home/firedrake/notebooks,type=bind shape-notebook
```

This binds host notebook folder with docker's notebook folder so that we can persist notebooks across sessions.



P.S. the only predictable issues related with installation lie on the image of firedrake used as base image. There's no obvious workaround, as they only keep the latest version available in docker. If you are having troubles installing or running the code, then use firedrake's recipe to create their docker image in a commit around 02/06/2023.
