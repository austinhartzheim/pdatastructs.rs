# Contributing

**Unless you explicitly state otherwise, any contribution you intentionally submit for inclusion in the work, as
defined in the Apache-2.0 license, shall be dual-licensed as above, without any additional terms or conditions.**

## Tests
To run the tests, simply run:

```bash
cargo test
```

There are two variants of tests, unit tests and doctests.

The unit tests are added inline as an additional test module:

```rust
#[cfg(test)]
mod tests {
    use super::GreatThing;

    #[test]
    fn test_getters() {
        let thing = GreatThing::new(1);
        assert_eq!(thing.number(), 1);
    }
}
```

Doctests are added to traits and structs to illustrate their usage:

```rust
/// A thing to have
///
/// # Examples
/// ```
/// use tdigest::thing::GreatThing;
///
/// let thing = GreatThing::new(1);
/// thing.do_something();
/// ```
struct GreatThing {}
```

## Benchmarks
Apart from the normal tests, please note that also the benchmarks must pass. You can test this (without actually
benchmarking) using:

```bash
cargo bench --verbose --all -- --test
```

The benchmarks are implemented using [criterion.rs](https://github.com/bheisler/criterion.rs). To benchmark the library,
run:

```bash
cargo bench
```

## Formatting
Use [rustfmt](https://github.com/rust-lang/rustfmt) to format the code:

```bash
cargo fmt
```

## Clippy / Linting
It would be nice if you could follow [clippy](https://github.com/rust-lang/rust-clippy) loosely and take its
recommendation into account, although passing this linter is currently not a hard requirement.

```bash
cargo clippy
```

There are however some lints provided by `rustc` which needs to be fulfilled:

- [`anonymous_parameters`](https://doc.rust-lang.org/rustc/lints/listing/allowed-by-default.html#anonymous-parameters)
- [`bare_trait_objects`](https://doc.rust-lang.org/rustc/lints/listing/allowed-by-default.html#bare-trait-object)
- [`const_err`](https://doc.rust-lang.org/rustc/lints/listing/warn-by-default.html#const-err)
- [`dead_code`](https://doc.rust-lang.org/rustc/lints/listing/warn-by-default.html#dead-code)
- [`illegal_floating_point_literal_pattern`](https://doc.rust-lang.org/rustc/lints/listing/warn-by-default.html#illegal-floating-point-literal-pattern)
- [`missing_debug_implementations`](https://doc.rust-lang.org/rustc/lints/listing/allowed-by-default.html#missing-debug-implementations)
- [`missing_docs`](https://doc.rust-lang.org/rustc/lints/listing/allowed-by-default.html#missing-docs)
- [`non_camel_case_types`](https://doc.rust-lang.org/rustc/lints/listing/warn-by-default.html#non-camel-case-types)
- [`non_snake_case`](https://doc.rust-lang.org/rustc/lints/listing/warn-by-default.html#non-snake-case)
- [`non_upper_case_globals`](https://doc.rust-lang.org/rustc/lints/listing/warn-by-default.html#non-upper-case-globals)
- [`unknown_lints`](https://doc.rust-lang.org/rustc/lints/listing/warn-by-default.html#unknown-lints)
- [`unreachable_code`](https://doc.rust-lang.org/rustc/lints/listing/warn-by-default.html#unreachable-code)
- [`unreachable_patterns`](https://doc.rust-lang.org/rustc/lints/listing/warn-by-default.html#unreachable-patterns)
- [`unreachable_pub`](https://doc.rust-lang.org/rustc/lints/listing/allowed-by-default.html#unreachable-pub)
- [`unsafe_code`](https://doc.rust-lang.org/rustc/lints/listing/allowed-by-default.html#unsafe-code)
- [`unused_extern_crates`](https://doc.rust-lang.org/rustc/lints/listing/allowed-by-default.html#unused-extern-crates)

## Documentation
The documentation of data structures uses the following style:

```markdown
A simple introduction what this data structure can do. Math is represented as code (`x = a + b`).

# Examples
\`\`\`
use pdatastructs::foo::MyStructure;

// set up data structure
let param1 = 0.2;
let param2 = true;
let mut whatever = MyStructure::new(param1, param2);

// add some data
whatever.add(&"my super long string");

// later
assert!(whatever.can_do_something());
\`\`\`

# Applications
- list some theoretical and known real world applications

# How It Works
Explain, how the data structure works.

\`\`\`text
might use some nice ASCII diagrams

+-------++---+---+---+---+---+---+---+---+
| block || 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|  data ||   |   |   |   |   |   |   |   |
+-------++---+---+---+---+---+---+---+---+
\`\`\`

## Insertion
Explain insertion...

## Query
Explain query...

# See Also
- link to data structures that are similar in standard library, this library, 3rd-party libs

# References
- ["Title", Author1, Author2, Year](https://some-open-access.net/foo/bar)
- [Wikipedia: Data Structure](https://en.wikipedia.org/wiki/Data_structure)
```

Sometimes, you may need some mathematical plots to illustrate certain things. Use [gnuplot](http://www.gnuplot.info/) to
create these. First, setup a terminal plotter:

```text
unset key
set term dumb feed 60, 20
```

Optionally, set the range for the plot:

```text
set xrange [0:1]
```

Finally, create a plot and copy the output to the markdown documentation:

```text
plot x * x + 10
```
