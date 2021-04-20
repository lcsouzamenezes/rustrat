# RustRAT

RustRAT is a project to write a **R**emote **A**ccess **T**rojan in Rust.
For more details about the project, see https://www.wodinaz.com/.

This repository contains several folders with different projects.
* rustrat-client The RAT itself
* rustrat-server The server listening for incoming connections (not written yet)
* payloads Projects that compiles down to WebAssembly for execution and helper libraries for payload creation

## Build instructions
If the database schema is changed, a new example database needs to be created. First the code in rustrat-server to initialize an empty database must be updated, then a new example database must be created. This can be accomplished by executing the following commands:

* `cargo run --bin update-dbtemplate`
* `cargo sqlx -D sqlite://rustrat-server/dbtemplate.sqlite3?mode=ro prepare --merged`

## Usage
* `rustrat-client-exe.exe path\to\webassembly.wasm function_name`
* `rundll32 rustrat_client.dll,rundll_run path\to\webassembly.wasm function_name`

Note that the functionality to execute compiled WebAssembly will be moved to a separate crate for development/debugging purposes.