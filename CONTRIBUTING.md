# Contributing to the Open and REprOducible NeuroImaging 

## Adding a resource to the book

Our list of resources is available [here]() but we may have missed some 
or there may be some new ones that have appeared since the last update.

If you want to add a resource to our resource list, please use [our form](https://github.com/agahkarakuzu/oreoni/issues/new?assignees=&labels=&template=feature_request.yml&title=%5BENH%5D+) to open an issue and we will get back to you.
<!-- TODO update URL if the repo moves -->

<!-- TODO a clear list of criterion to accept a new resource -->

## Building the book locally

_Requirements_

- Python

Clone the reposity

```bash
git clone https://github.com/agahkarakuzu/oreoni.git
cd oreoni
```

Install all the required packages:

```bash
pip install -r requirements.txt
```

```bash
jupyter-book build content
```

If you are using a Linux distribution, you can use the following commands

- to install the required packages AND build the book:

```bash
make install
```

- to build the book:

```bash
make book
```

Type `make help` to see the list of available commands.
