# Multi-party ECDSA

This project is a Typescrypt & Rust implementation of {t,n}-threshold ECDSA (elliptic curve digital signature algorithm) for Teleport bridge protocol.

CAUTION: Current project is for testing in local environment without any containers, and will be updated soon

## Library Introduction
The library was built with four core design principles in mind:
1. Multi-protocol support
2. Build mpc oracle nodes for teleport bridge
3. Testing purpose

### Setup

1. You need [Rust](https://rustup.rs/) and [GMP library](https://gmplib.org) (optionally) to be installed on your computer.
2. - Run `cargo build --release --examples`
   - Don't have GMP installed? Use this command instead: 
     ```bash
     cargo build --release --examples --no-default-features --features curv-kzen/num-bigint
     ```
     But keep in mind that it will be less efficient.

   Either of commands will produce binaries into `./target/release/examples/` folder.

## Run GG18 sm_manger 

- Run  `cd sm_manager`
- Run `cargo build --release --examples`
- Run `./target/release/examples/gg18_sm_manager`

### Run fist mpc node 

- Run `cd mpc_node_0`
- Run `pnpm install`
- Run `cd ./src/multiparty`

build multiparty library
- Run `cargo build --release --examples`
Once build is done, move /target/release/examples and edit client name
i.e. gg18_sign_client -> gg18_sign_client0 (0 is index of mpc node)

edit env variables according to example.env file

### Run second mpc node

Build second node accordig to above instruction

#### Example
Once two sm_sign_manager, and two mpc nodes are running successfully, you can test sign function by send http request
Please refer to ./requests

## References

[1] <https://eprint.iacr.org/2017/552.pdf>

[2] <https://eprint.iacr.org/2019/114.pdf>

[3] <https://eprint.iacr.org/2019/503.pdf>

[4] <https://eprint.iacr.org/2020/540.pdf>
