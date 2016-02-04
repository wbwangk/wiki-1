# Parity

### Quick Start with Docker

Docker's great for making sure differences between operating systems, distributions, installations and build environments don't get in the way of coding fun. For a quick start, we'll just use docker to set up a minimal Ubuntu installation and take it from there. You can use similar instructions to get things working on pretty much any Linux installation or a Mac Homebrew system, but that's left as an exercise to the reader for now.

*NOTE*: Ensure you have docker to begin with.

```
docker run -it ubuntu bash
```

This will give you a temporary docker environment.

Next grab curl.

```
apt-get install curl -y
```

Then run the dependency install script:

```
bash <(curl https://raw.githubusercontent.com/ethcore/parity/master/install-deps.sh -L)
```

This will download and install all the build dependencies, in our case, that's Git, Make and GCC/G++, librocksdb, and Rust nightly.

Next, grab the parity repository:

```
git clone git@github.com:ethcore/parity && cd parity
```

You can build with:

```
cargo build
```

You can run the unit tests with:

```
cargo test --release -p ethcore-util && cargo test -p ethcore
```

You can run the consensus tests with:

```
cargo test --release --features ethcore/json-tests -p ethcore
```

You can start a client and sync with the network with:

```
cargo run --release
```

To get help on the command line options for the `parity` client, use `--help`:

```
cargo run --release -- --help
```

Have fun.



