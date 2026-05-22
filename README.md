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
* Docker Compose v5.0.1 or newer
* Cargo 1.92.0 or newer

## Target Environment:
* A bare-metal compute cluster composed of five single-board computers (AArch64)

# How to Run Locally
1. Clone the repo
```
git clone https://github.com/lucasthormann/rustfs.git
```

2. Build the PostgreSQL container image
```
docker compose up
```

3. Step into the backend directory && build/run it
```
cd backend && cargo run
```

4. Step into the frontend directory && build it
```
cargo build --target wasm32-unknown-unknown
```

5. Use Trunk to serve the GUI
```
trunk serve
```
