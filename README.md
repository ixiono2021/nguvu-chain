# NGUVU Node built with parity-substrate 

This is a nominated proof of stake blockchain with a native token called `NGV` built with the help of substrate.

## Building this node

### Rust Setup

First, make sure you have rust installed. We show you how to do this on Ubuntu but you can use this script if you're on another OS. This also installs `subkey` if you want to generate your own key pairs:

```bash
curl https://getsubstrate.io -sSf | bash -s -- --fast
```

Optional: If you want subkey as well run this
```sh
cargo install --force subkey --git https://github.com/paritytech/substrate --version 2.0.1 --locked
```
Navigate to the source code folder and run it:

### Run

Use Rust's native `cargo` command to build and launch the node:

```sh
cargo run --release -- --dev --tmp
```

### Build

The `cargo run` command will perform an initial build. Use the following command to build the node
without launching it:

```sh
cargo build --release
```

Congratulations you now have a working now. Note that if you built this node you can find it at ```target/release/nguvu```

### Embedded Docs

Once the project has been built, the following command can be used to explore all parameters and
subcommands:

```sh
./target/release/nguvu -h
```

## Run

The provided `cargo run` command will launch a temporary node and its state will be discarded after
you terminate the process. After the project has been built, there are other ways to launch the
node.

### Single-Node Development Chain with Staking enabled

This command will start the single-node development chain without a persistent state:

```bash
./target/release/nguvu --chain=stakingRaw.json
```
To start a node with persistent state make a directory to hold your chain data, which will include keys and the database
```bash
mkdir my_chain
./target/release/nguvu --chain=stakingRaw.json --base-path my_chain
```

Purge the development chain's state if you didn't use the `--tmp` flag earlier:

```bash
./target/release/nguvu purge-chain --dev
```

Start the development chain with detailed logging:

```bash
RUST_BACKTRACE=1 ./target/release/nguvu -ldebug --dev
```

### Connect with Polkadot-JS Apps Front-end Block Explorer

Once the node is running locally, you can connect it with [**Polkadot-JS Apps** front-end](https://polkadot.js.org/apps/?rpc=ws%3A%2F%2Flocalhost%3A9944#/explorer)
to interact with your chain.

Or run it locally: [Download the polkadot js apps Appimage](https://github.com/polkadot-js/apps/releases) and run it locally on a separate terminal. Then connect to `127.0.0.1:9944` which is the default websocket port used by substrate chains. 

