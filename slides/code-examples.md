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

<!-- ```rust
fn main() {
  let mut test: [i32; 3] = [0; 3];

  test[1] = 1;
  test[2] = 2;

  for x in &test {
      println!("Current number is: {} ", x);
  }
}
``` -->
