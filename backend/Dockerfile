# --- Stage 1: Builder ---
# Use an official Rust image as the base for building
FROM rust:latest AS builder

# Set the working directory in the container
WORKDIR /app

# Install necessary system dependencies (e.g., for openssl if your project uses it)
# The packages may vary based on your specific crates
RUN apt-get update && apt-get install -y pkg-config libssl-dev

# Copy Cargo.toml and Cargo.lock first to leverage Docker cache for dependencies
COPY Cargo.toml Cargo.lock ./

# A common optimization is to use a tool like cargo-chef for better dependency caching
# If not using cargo-chef, you can build a dummy project here to cache dependencies

# Copy the rest of the source code
COPY src ./src

# Build the release binary
RUN cargo build --release

# --- Stage 2: Runtime ---
# Use a minimal base image for the final, lean runtime
FROM debian:stable-slim

# Install runtime dependencies if needed (e.g., libssl)
RUN apt-get update

# Set the working directory
WORKDIR /app

# Copy only the compiled binary from the builder stage
COPY --from=builder /app/target/release/backend .

# Expose the port your API listens on (e.g., 8000)
EXPOSE 8000

# Command to run the application when the container starts
CMD ["./backend"]
