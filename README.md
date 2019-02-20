# rust-sysfs-pwm

[![Build Status](https://travis-ci.org/rust-embedded/rust-sysfs-pwm.svg?branch=master)](https://travis-ci.org/posborne/rust-sysfs-pwm)
[![Version](https://img.shields.io/crates/v/sysfs-pwm.svg)](https://crates.io/crates/sysfs-pwm)
[![License](https://img.shields.io/crates/l/sysfs-pwm.svg)](https://github.com/posborne/rust-sysfs-pwm/blob/master/README.md#license)

- [API Documentation](http://posborne.github.io/rust-sysfs-pwm/)

rust-sysfs-pwm is a rust library/crate providing access to the [Linux
sysfs PWM interface](https://www.kernel.org/doc/Documentation/pwm.txt).
It seeks to provide an API that is safe, convenient, and efficient.

## Install/Use

To use `sysfs-pwm`, first add this to your `Cargo.toml`:

```toml
[dependencies]
# or latest version
sysfs-pwm = "^0.1.0"
```

Then, add this to your crate root:

```rust
extern crate sysfs_pwm;
```

## Example/API

The main API consists of a Pwm struct with the following methods:
* `Pwm::new` - Create a Pwm instance
* `pwm.with_exported` - Execute a block with the Pwm exported
* `pwm.set_active` - Enable/Disable the Pwm
* `pwm.get_duty_cycle` - Get duty cycle as percentage of period
* `pwm.set_duty_cycle` - Set duty cycle as percentage of period
* `pwm.get_duty_cycle_ns` - Get duty cycle in nanoseconds
* `pwm.set_duty_cycle_ns` - Set duty cyle in nanoseconds
* `pwm.get_period_ns` - Get the Pwm period in nanoseconds
* `pwm.set_period_ns` - Set the Pwm period in nanoseconds

Check out the [Breathing LED](examples/breathe.rs) example for a usage
example.

## Cross Compiling

Most likely, the machine you are running on is not your development
machine (although it could be).  In those cases, you will need to
cross-compile.  The [instructions here][rust-cross] provide great details on cross
compiling for your platform.

[rust-cross]: https://github.com/japaric/rust-cross

## Running the Example

Cross-compiling can be done by specifying an appropriate target.  You
can then move that to your device by whatever means and run it.

```
$ cargo build --target=arm-unknown-linux-gnueabihf --example breathe
$ scp target/arm-unknown-linux-gnueabihf/debug/examples/breathe ...
```

## License

Licensed under either of

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or
  http://www.apache.org/licenses/LICENSE-2.0)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.

## Code of Conduct

Contribution to this crate is organized under the terms of the [Rust Code of
Conduct][CoC], the maintainer of this crate, the [Embedded Linux Team][team], promises
to intervene to uphold that code of conduct.

[CoC]: CODE_OF_CONDUCT.md
[team]: https://github.com/rust-embedded/wg#the-embedded-linux-team
