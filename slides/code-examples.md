JavaScript
```js

  const test = [0]

  test.push('hi')
  test.push(2)

  test.forEach(i => console.log(`Current item is: ${i}`))


```

---

Ruby
```ruby

  test = [0]

  test.push('hi')
  test.push(2)

  test.each { |i| puts "Current item is: #{i}" }


```

---

# 🤯

---

Rust

```rust

  fn main() {
    let mut test: [i32; 3] = [0; 3];

    test[1] = 1;
    test[2] = 2;

    for x in &test {
        println!("Current number is: {} ", x);
    }
  }


```

---

Rust: Ownership

```rust

  fn main() {
      let s1 = String::from("hello");
      let s2 = s1;

      println!("{}, world!", s1); // error!
  }


```

---

Rust: the compiler

```text
error[E0382]: use of moved value: `s1`
 --> src/main.rs:5:28
  |
3 |     let s2 = s1;
  |         -- value moved here
4 |
5 |     println!("{}, world!", s1);
  |                            ^^ value used here after move
  |
= "note": move occurs because `s1` has type `std::string::String`, which does
  not implement the `Copy` trait
```
