## Threads

---

Problema: si el jugador espera input indefinidamente deberia morirse, pero hasta que no vuelve a realizar una acción no se miran los stats.

---

### 3 threads

<ul>
  <li class="fragment">Input</li>
  <li class="fragment">Control time</li>
  <li class="fragment">Main</li>
</ul>

---

### Communication between threads

- Shared Messages

- Shared State

---

### Messages

```rust
let (tx, rx) = mpsc::channel();
```

---

## 🌲👂

---

Si un arbol cae en el bosque y no hay nadie escuchando, hace ruido?

En js cuando envias un mensaje si no hay nadie escuchando se pierde

En Rust, el arbol no cae hasta que hay alguien para escucharlo.

Y si no hay nadie arde el bosque entero

---

### State

Mutex (mutual exclusion)

---

```rust

  let stats = Arc::new(Mutex::new(Stats {
      water: Stat::new(100.0),
      food: Stat::new(100.0),
      energy: Stat::new(100.0),
      health: Stat::new(100.0)
  }));

```

---

```rust

  stats.lock().unwrap()

```
 it does unlock automatically when it goes "out of scope"
---

