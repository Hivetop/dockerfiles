FROM rust:alpine

RUN apk add --update build-base npm tar

RUN rustup target add wasm32-unknown-unknown
RUN rustup default nightly
RUN rustup component add clippy

RUN cargo install wasm-pack
RUN cargo install trunk
RUN cargo install cargo-llvm-cov

