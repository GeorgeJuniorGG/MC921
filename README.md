# MC921

Construction of Compilers

## Table of Contents

+ tests: unit tests
+ uc: source code for our uc (micro C) compiler

## Requirements

Use Python 3.7 or a newer version.Required pip packages:

- ply, pytest, setuptools, graphviz, pathlib

### Docker

Alternatively you can also use Docker & Docker Compose (Docker Engine 19.03.0+) if you don't
want to setup a local environment.

## Running

You can run `uc_analysis.py` directly with python. For more information, run:

```sh
    python3 uc/uc_analysis.py -h
```

You can use the inputs available inside
the `tests/in-out/` directory.

The `uc_compiler.py` script is also available, it can be run through its
symbolic link at the root of the repo (`ucc`). For more information, run:

```sh
    ./ucc -h
```

### Docker

If you're using the dockerized environment, to run `uc_code.py` directly you should run:

```sh
docker-compose run --rm test uc/uc_code.py -h
```

```sh
# Example: running test 01
docker-compose run --rm test uc/uc_code.py tests/in-out/t01.in
```

## Testing with Pytest

You can run all the tests in `tests/in-out/` automatically with `pytest`. For
that, you first need to make the source files visible to the tests. There are
two options:

- Install your project in editable mode using the `setup.py` file from the root
  of the repo

```sh
    pip install -e .
```

- Or, add the repo folder to the PYTHONPATH environment variable with `setup.sh`

```sh
    source setup.sh
```

### Docker

Running all tests in the dockerized environment:

```sh
# When installing Docker on linux, this is a way you can use compose.
# For Mac and Windows, don't forget the hyphen on docker-compose.
docker compose run --rm pytest
```

Then you should be able to run all the tests by running `pytest` at the root
of the repo.

### Linting and Formatting

This step is **optional**. Required pip packages:

- flake8, black, isort

You can lint your code with two `flake8` commands from the root of the repo:

```sh
    flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics
    flake8 . --count --exit-zero --max-line-length=120 --statistics
```

The first command shows errors that need to be fixed and will cause your
commit to fail. The second shows only warnings that are suggestions for
a good coding style.

To format the code, you can use `isort` to manage the imports and `black`
for the rest of the code. Run both from the root of the repo:

```sh
    isort .
    black .
```

## About

This repository is one of the assignments handed out to the students in the course
"MC921 - Compiler Construction" offered by the Institute of
Computing at Unicamp.
