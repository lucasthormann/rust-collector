# Email Address Aggregator
* A full-stack application designed to aggregate/collect email addresses that is implemented in Rust 1.92.0.

## Development Environment
* Lenovo T14 Gen 6 (x86_64)
* Ubuntu 24.04.3
* GNOME Terminal 3.52.0
* Vi IMproved 9.1

## Dependencies:
* Git 2.43.0 or newer
* Docker 28.2.2 or newer
* Docker Compose 5.0.1 or newer
* Cargo 1.92.0 or newer
* wasm32-uknown-uknown (WebAssembly compilation target)
* Trunk 0.21.14

## Target Environment:
* A bare-metal compute cluster composed of five single-board computers (AArch64) running a Debian 13 instance

# How to Run Locally
1. Clone the repo
```
git clone https://github.com/lucasthormann/rustfs.git
```

2. Start the container and run the PostgreSQL instance
```
docker compose up
```

3. Step into the backend directory && compile/run the package
```
cd backend && cargo run
```

4. Step into the frontend directory && compile the package
```
cargo build --target wasm32-unknown-unknown
```

5. Use Trunk to serve the GUI
```
trunk serve
```
