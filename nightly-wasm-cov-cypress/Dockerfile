FROM cypress/browsers:latest

# Rust stuff
ENV RUSTUP_HOME=/usr/local/rustup \
    CARGO_HOME=/usr/local/cargo \
    PATH=/usr/local/cargo/bin:$PATH \
    RUST_VERSION=1.75.0

RUN apt-get update
RUN apt-get install -y --no-install-recommends \
        ca-certificates \
        gcc \
        libc6-dev \
        wget \
        curl \
        git \
        libnss-myhostname \
        tar

RUN set -eux; \
    url="https://static.rust-lang.org/rustup/archive/1.26.0/x86_64-unknown-linux-gnu/rustup-init"; \
    wget "$url"; \
    chmod +x rustup-init; \
    ./rustup-init -y --no-modify-path --profile minimal --default-toolchain $RUST_VERSION --default-host "x86_64-unknown-linux-gnu"; \
    rm rustup-init; \
    chmod -R a+w $RUSTUP_HOME $CARGO_HOME;

RUN rustup default nightly
RUN rustup component add clippy
RUN rustup component add rustfmt

RUN cargo install wasm-pack
RUN cargo install trunk
RUN cargo install cargo-llvm-cov

RUN rustup target add wasm32-unknown-unknown
