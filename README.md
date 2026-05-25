# Rust Collector
* A full-stack application, designed for quick aggregation/collection of email addresses, that is implemented in Rust (1.92.0).

## Development Environment
* Lenovo T14 Gen 6 (x86_64)
* Ubuntu (24.04.3)
* GNOME Terminal (3.52.0)
* Vi IMproved (9.1)

## Dependencies:
* Git (2.43.0 or newer)
* Docker (28.2.2 or newer)
* Docker Compose (5.0.1 or newer)
* Rustup (1.28.2 or newer)
* Cargo (1.92.0 or newer)
* Trunk (0.21.14)

## Target Environment:
* A bare-metal compute cluster composed of five single-board computers that contain the Broadcom BCM2711 SoC (AArch64) and are running a Debian (13.2) instance

## Container Images:
* Frontend: https://hub.docker.com/r/lucasthormann/k3s-rust-frontend
* Backend: https://hub.docker.com/r/lucasthormann/k3s-rust-backend

# How to Run Locally
1. Clone the repo
```
git clone https://github.com/lucasthormann/rust-collector.git
```

2. Start the container and run the PostgreSQL instance within it
```
docker compose up
```

3. Install the WebAssembly 32-bit compilation target
```
rustup target add wasm32-unknown-unknown
```

4. Step into the backend directory & compile then run the package
```
cd backend && cargo run --release
```

5. Step into the frontend directory & compile the package to a WebAssembly (1.0) module
```
cargo build --release --target wasm32-unknown-unknown
```

6. Use Trunk to build, bundle, & serve the GUI
```
trunk serve --release
```

7. Access the application via a modern web browser using this URL
```
http://localhost:8080
```
