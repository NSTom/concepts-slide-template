---
author: The authors
title: Concepts of programming languages
subtitle: Language XXXX
theme: uucs
monofontoptions: Scale=0.75
monofont: Fira Mono
mainfont: Fira Sans Light
sansfont: Fira Sans Light
---

# What problems does Rust (intent to) solve?

* Memory safety
* "Fearless" concurrency
* Performance

---

# Memory safety
## Null pointers
* Easy to forget
* The Option enum (similar to Maybe in Haskell)
* The Result enum

---

# Memory safety
## Null pointers
```rust
enum Option<T> {
    Some(T),
    None,
}
enum Result<T, E> {
 Ok(T),
 Err(E),
}

```

---

# Memory safety
## Dangling references
* No garbage collector!
* Borrowing rules/Lifetimes

---

# Memory safety
## Buffer overruns
* Safety
* Index in array
* Compile/Runtime checks

---

# "Fearless" concurrency
## Borrowing rules
* Only one owner
* No aliassing
* Easier debugging

---

# "Fearless" concurrency
## Message passing
```rust
let (tx, rx) = mpsc::channel();

thread::spawn(move || {
    let val = 5;
    tx.send(val).unwrap();
});

let received = rx.recv().unwrap();
```

---

# "Fearless" concurrency
## Shared state
```rust
let m = Mutex::new(0);

thread::spawn(move || {
    let mut num = m.lock().unwrap();
    *num = 5;
});
```

---

# Performance
* No garbage collector
* Fewer run time checks
