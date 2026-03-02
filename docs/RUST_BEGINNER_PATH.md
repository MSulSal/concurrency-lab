# Rust Beginner Path (Lab-Oriented)

This guide keeps Rust learning tied to project outcomes, not abstract syntax drills.

## 1. Learning Strategy

- Learn just enough Rust for the current project.
- Ship code in small increments.
- Use compiler errors as teaching feedback.
- Prefer correctness and clarity first, then performance.

## 2. Core Rust Mental Model

- Ownership: each value has one owner.
- Borrowing: pass references (`&T`, `&mut T`) instead of moving when needed.
- Lifetimes: compiler proof that references stay valid.
- Mutability: explicit (`mut`), immutable by default.
- Error handling: `Result<T, E>` and `?` operator.
- Enums + pattern matching: model states and outcomes safely.

## 3. Tooling You Will Use Daily

```powershell
cargo check
cargo run
cargo test
cargo fmt
cargo clippy -- -D warnings
```

## 4. Rust-by-Project Map

- `P00`: CLI parsing, structs, `Vec`, loops, file I/O, `Result`.
- `P01-P05`: threads, `Mutex`, `RwLock`, `Condvar`, channels.
- `P06-P11`: traits, modules, generics, atomics, memory ordering.
- `P12+`: protocol modeling, state machines, serialization, fault injection.

## 5. Beginner Rules (Strict)

1. `cargo check` before each commit.
2. Avoid `unwrap()` in core logic; return errors with context.
3. Keep functions small and explicit about inputs/outputs.
4. Prefer simple data structures before "clever" abstractions.
5. Add one test for each bug fixed.

## 6. What to Learn Next (Ordered)

1. Ownership and borrowing basics.
2. `struct` and `enum` design.
3. `Result` and error propagation.
4. Iterators vs loops.
5. Threads and shared state primitives.
6. Atomics and memory ordering.

## 7. Fast Troubleshooting

- "value moved": pass by reference or clone intentionally.
- "cannot borrow as mutable": ensure unique mutable borrow at that scope.
- "lifetime may not live long enough": return owned data instead of references where possible.
- "trait bound not satisfied": check type requirements on generics.

## 8. Definition of Success for Beginner Phase

You can read a Rust compile error, explain it, and fix it without guessing.
