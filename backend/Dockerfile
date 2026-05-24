# --- Stage 1: Builder ---
# Use an official Rust image as the base for building
FROM rust:latest AS builder

# Set the working directory in the container
WORKDIR /app

# Install necessary system dependencies
RUN apt-get update && apt-get install -y pkg-config libssl-dev

# Copy Cargo.toml and Cargo.lock first to leverage Docker cache for dependencies
COPY Cargo.toml Cargo.lock ./

# Copy the rest of the source code
COPY src ./src

# Build the release binary
RUN cargo build --release

# --- Stage 2: Runtime ---
# Use a minimal base image for the final, lean runtime
FROM debian:stable-slim

# Install runtime dependencies
RUN apt-get update

# Set the working directory
WORKDIR /app

# Copy only the compiled binary from the builder stage
COPY --from=builder /app/target/release/backend .

# Expose the port the API listens on
EXPOSE 8000

# Command to run the application when the container starts
CMD ["./backend"]
