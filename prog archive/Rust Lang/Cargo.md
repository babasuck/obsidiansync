*Cargo.toml* файл - метаинформация о проекте в формате [TOML](https://toml.io/en/) 

```toml
[package]
name = "hello_cargo" 
version = "0.1.0"
edition = "2021"

[dependencies]
```

## Основные команды
```shell
cargo init # create cargo.toml
cargo new name # create project
cargo build # build (compile link etc)
cargo build --release # in release mode (faster)
cargo run # build + run
cargo check # check if compiles w/o create exe
```

