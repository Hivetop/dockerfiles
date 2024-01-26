FROM rust:alpine

RUN apk add --update build-base npm tar git bash
RUN wget https://dl-cdn.alpinelinux.org/alpine/edge/testing/x86_64/dartaotruntime-3.2.5-r0.apk
RUN wget https://dl-cdn.alpinelinux.org/alpine/edge/testing/x86_64/dart-sass-1.70.0-r0.apk
RUN apk add dartaotruntime-3.2.5-r0.apk
RUN apk add dart-sass-1.70.0-r0.apk

RUN rustup default nightly
RUN rustup component add clippy
RUN rustup component add rustfmt

RUN cargo install wasm-pack
RUN cargo install trunk
RUN cargo install cargo-llvm-cov
RUN rustup target install wasm32-unknown-unknown

