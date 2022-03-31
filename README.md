rustfmt-nightly
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
====================================================================================================

***Scripted build and install of rustfmt using the Rust nightly container***

### Quick links
* [Usage](#usage)
  * [Dependencies](#dependencies)
  * [Scripted install](#scripted-install)
  * [Manually install](#manually-install)
* [License](#license)
  * [Contributions](#contributions)
* [Changelog](#changelog)

# Usage

## Dependencies
You'll need the following nix dependencies installed and configured

* git
* jq
* curl
* docker - assumes your user is configured to run docker

## Scripted install

1. Clone this repo and switch to your local clone
   ```bash
   $ git clone https://github.com/phR0ze/rustfmt-bin
   $ cd rustfmt-bin
   ```

2. Run the script to build and install rustfmt
   ```bash
   $ ./install
   ```

## Manually install

1. Clone this repo and switch to your local clone
   ```bash
   $ git clone https://github.com/phR0ze/rustfmt-bin
   $ cd rustfmt-bin
   ```

2. Determine the [latest rustfmt release](https://github.com/rust-lang/rustfmt/releases)

3. Clone the rustfmt source locally using the target version
   ```bash
   $ git clone -b v1.4.38 --single-branch https://github.com/rust-lang/rustfmt
   ```

4. Build the source using Rust nightly docker image
   ```bash
   $ alias rust-nightly-builder='docker run --rm -it -v "$(pwd)/rustfmt":/usr/src -w=/usr/src rustlang/rust:nightly'
   $ rust-nightly-builder cargo build --release
   ```

5. Install built rustfmt
   ```bash
   $ sudo cp rustfmt/target/release/rustfmt /usr/bin
   $ cp rustfmt/target/release/rustfmt ~/.cargo/bin
   $ cp rustfmt/target/release/cargo-fmt ~/.cargo/bin
   ```

# License
This project is licensed under either of:
 * MIT license [LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT
 * Apache License, Version 2.0 [LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0

## Contributions
Pull requests are always welcome. However understand that they will be evaluated purely on whether
or not the change fits with my goals/ideals for the project.

Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in
this project by you, shall be dual licensed as above, without any additional terms or conditions.

---

# Changelog
