## Threads

---

### 3 threads

<ul>
  <li class="fragment">Control time</li>
  <li class="fragment">Input</li>
  <li class="fragment">Main</li>
</ul>

---

### Create a thread

```rust

  thread::spawn(move || loop {
      thread::sleep(Duration::from_secs(10));
      println!("Now we should decrease stats…");
  });


```

---

### Decrease stats: Shared state

```rust

  fn main() {
      let stats = Arc::new(Mutex::new(Stats {
          water: Stat::new(100.0),
          food: Stat::new(100.0),
          energy: Stat::new(100.0),
      }));

      control_time(&stats);

      // ...
  }


```

---

```rust

  fn control_time(stats: &Arc<Mutex<Stats>>) {
      let stats = Arc::clone(&stats);

      thread::spawn(move || loop {
          thread::sleep(Duration::from_secs(10));
          let mut stats_lock = stats.lock().unwrap();
          decrease_stats(&mut stats_lock, 10.0);
      });
  }


```

---

<img src="./public/leap.gif" alt="leap of faith" style="height: 35vh">

---

### Handle input

<ul>
  <li class="fragment">
    Input Thread:
    <ul>
      <li>asks user for input</li>
    </ul>
  </li>
  <li class="fragment">Main Thread:
   <ul>
      <li>receives input</li>
      <li>asks input thread for more</li>
    </ul>
  </li>
</ul>

---

### Messages

```rust

  let (tx, rx) = mpsc::channel();
  let (tx2, rx2) = mpsc::channel();


```

---

## 🌲👂

---

JavaScript

```js

  document.dispatchEvent(new CustomEvent('hi!'))


```

---

Rust

```rust

  tx.send("hi");

  // ...

  // rx.recv();


```

---

```rust

  thread::spawn(move || loop {
      let _ = rx2.recv();

      let action = request_input("\nWhat to do?");

      tx.send(action).ok();
  });


```

---

```rust

  loop {
      if let Ok(action) = rx.try_recv() {
          match action.trim() {
              // handle all possible actions
          }
      }
      if is_game_over(&stats.lock().unwrap()) {
          break;
      } else {
          tx2.send(String::from("Ready for input")).ok();
      }
  }


```


---

<video src="public/live-threads.mp4" loop data-autoplay controls />

---

```rust

  loop {
      if let Ok(action) = rx.try_recv() {
          match action.trim() {
              // handle all possible actions
          }
          // now we are ready for another action:
          tx2.send(String::from("Ready for input")).ok();
      }
      if is_game_over(&stats.lock().unwrap()) {
          break;
      }
  }


```

---

Overwhelmed?

![Scared Snow White](https://media.giphy.com/media/ETM2m9EI2pge4/giphy.gif)
