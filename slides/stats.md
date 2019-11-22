## Handle time
### Decrease stats and increase days

---

```js

  {
    startStatsTimer () {
      this.loop = setTimeout(() => {
        if (this.isActive) {
          this.decreaseStats()
          this.startStatsTimer()
        }
      }, 12 * 1000)
    }
  }


```

---

```rust

  let now = Instant::now();
  let mut elapsed_time = now.elapsed().as_secs();

  loop {
      let current_elapsed_time = now.elapsed().as_secs();
      let seconds = current_elapsed_time - elapsed_time;
      elapsed_time = current_elapsed_time;

      decrease_stats(&mut stats, seconds as f64);

      // Ask user for input ...
  }


```

---

![waiting for input](./public/waiting.png)
