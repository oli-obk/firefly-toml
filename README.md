# firefly-toml

A Rust macro for statically parsing [firefly.toml](https://docs.fireflyzero.com/dev/config/).

## Usage

It can be used through [firefly-rust](https://github.com/firefly-zero/firefly-rust) by activating `firefly-toml` crate feature:

```bash
cargo add firefly-rust --features firefly-toml
```

Which will add `firefly_rust::toml` module with the helpers based on the `firefly.toml` config:

```rust
use firefly_rust::toml;

toml::some_badge(peer, 123);
```

Or can be used directly via macro adding everything into the current scope:

```rust
mod toml {
    firefly_toml::import!();
}

toml::some_badge(peer, 123);
```

### Palettes

Every palette you specify in `firefly.toml` will have a method of that name in the `palettes` module.
The method will set the entire current color palette to what you have configured in `firefly.toml`.

### Files

Images, fonts and other files will have an initializer method that automatically fills in a global static with
the loaded file. After initialization you can access that file's static with `files::the_name`.

The type depends on the file extension, so if the extension is unknown, you'll just get a `FileRef`.
For known extensions you either get a `FontRef` or an `ImageRef`, whichever is appropriate.

## License

MIT License. You can do whatever you want with the code in here, modify it, embed into any apps and games. Have fun!

Originally developed by [oli-obk](https://github.com/oli-obk) and is currently officially maintained by the Firefly Zero core team.
