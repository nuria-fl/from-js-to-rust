## Ask user for input

---

```rust

    loop {
        let mut action = String::new();

        io::stdin()
            .read_line(&mut action)
            .ok()
            .expect("Failed to read line");

        match action.trim() {
            "scavenge" | "s" => scavenge(&mut inventory, &mut stats),
            // ...
            _ => println!("Invalid input"),
        }
    }

```
