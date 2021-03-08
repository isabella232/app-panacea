# Ledger Panacea app
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

This project contains the Panacea app for Ledger Nano S and X.

- Ledger Nano S/X Panacea app
- Specs / Documentation
- C++ unit tests


# Development

## Preconditions

- Be sure you checkout submodules too:

    ```
    git submodule update --init --recursive
    ```

- Install Docker CE
    - Instructions can be found here: https://docs.docker.com/install/

- We only officially support Ubuntu. Install the following packages:
   ```
   sudo apt update && apt-get -y install build-essential git wget cmake \
  libssl-dev libgmp-dev autoconf libtool
   ```

- Install `node > v13.0`. We typically recommend using `n`

- You will need python 3 and then run
    - `make deps`

- This project requires Ledger firmware 1.6
    - The current repository keeps track of Ledger's SDK but it is possible to override it by changing the git submodule.

*Warning*: Some IDEs may not use the same python interpreter or virtual enviroment as the one you used when running `pip`.
If you see conan is not found, check that you installed the package in the same interpreter as the one that launches `cmake`.

## How to build ?

> We like clion or vscode but let's have some reproducible command line steps
>

- Building the app itself

    If you installed the what is described above, just run:
    ```bash
    make
    ```

## Running tests

- Running rust tests (x64)

    If you installed the what is described above, just run:
    ```bash
    make rust_test
    ```

- Running C/C++ tests (x64)

    If you installed the what is described above, just run:
    ```bash
    make cpp_test
    ```


### Loading into your development device

The Makefile will build the firmware in a docker container and leave the binary in the correct directory.

- Build

   ```
   make                # Builds the app
   ```

- Upload to a device
   The following command will upload the application to the ledger. _Warning: The application will be deleted before uploading._
   ```
   make load          # Builds and loads the app to the device
   ```

## APDU Specifications

- [APDU Protocol](docs/APDUSPEC.md)
- [Transaction format](docs/TXSPEC.md)
