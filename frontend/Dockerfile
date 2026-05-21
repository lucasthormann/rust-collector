# Stage 1: Build the Rust/Wasm application and bundle assets
FROM rust:latest AS builder

# Install wasm-pack and other necessary tools in the builder image
RUN cargo install trunk

RUN rustup target add wasm32-unknown-unknown

WORKDIR /app

# Copy source code and perform build
COPY . .
 
RUN trunk build --release --dist ./dist

# Stage 2: Serve the static files using a lightweight server
# We use a minimal Nginx image for serving static content
FROM nginx:alpine AS runtime

# Copy the static files from the builder's output directory to the Nginx serving directory
# The default output for wasm-pack is 'pkg', for trunk it is 'dist'
COPY --from=builder /app/dist /usr/share/nginx/html

# Expose port 80 for web traffic
EXPOSE 80

# Nginx starts automatically as the default command
CMD ["nginx", "-g", "daemon off;"]

