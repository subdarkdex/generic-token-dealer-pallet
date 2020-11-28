# FRAME pallet - token dealer for fungible assets 


## Purpose

This pallet aims to provide functionalities for sending and handling transfer of tokens and currency between parachains and relay chain. 

___ 
## Dependencies

### Traits

This pallet depends on `frame-support/Currency`

### Pallets

[pallet-assets](https://github.com/subdarkdex/pallet-assets) is a forked substrate pallet-assets to ensure that the dependencies are compatable with the current cumulus template on which this is built on 


## Installation

### Runtime `Cargo.toml`

To add this pallet to your runtime, simply include the following to your runtime's `Cargo.toml` file:

```TOML
[dependencies.substrate-pallet-generic-token-dealer]
default_features = false
git = 'https://github.com/subdarkdex/pallet-generic-token-dealer'
```

and update your runtime's `std` feature to include this pallet:

```TOML
std = [
    # --snip--
    'pallet-generic-token-dealer/std',
]
```

### Runtime `lib.rs`

You should implement it's trait like so, please see mock.rs for details:

```rust
/// Used for test_module
impl Trait for TokenDealer {
    type UpwardMessageSender = MessageBrokerMock;
    type UpwardMessage = TestUpwardMessage;
    type XCMPMessageSender = MessageBrokerMock;
    type Event = TestEvent;
    type Currency = Balances;
}

```

and include it in your `construct_runtime!` macro:

```rust
TokenDealer: generic_token_dealer::{Module, Call, Storage, Event<T>},
```

### Genesis Configuration

This template pallet does not have any genesis configuration.

## Reference Docs

You can view the reference docs for this pallet by running:

```
cargo doc --open
```

