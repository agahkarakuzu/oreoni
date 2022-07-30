# Contributing to the Open and REprOducible NeuroImaging book

## Building the book locally

_Requirements_

- Python

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
