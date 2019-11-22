## Inventory

---

### Vectors

```rust

  type Inventory = Vec<Item>

  let mut inventory: Inventory = Vec::new();

  // ...

  inventory.push(item);


```

---

### Items

<div style="display: grid; grid-template-columns: 1fr 1fr 1fr; font-size: 5rem;">
  <div class="fragment">
    📎
  </div>
  <div class="fragment">
    🍒
  </div>
  <div class="fragment">
    🔪
  </div>
</div>

---

### Structs

```rust

  struct Item {
      name: &'static str,
      description: &'static str,
      value: ItemStats,
      risk: f64,
      uses_until_breakdown: i32,
      consumable: bool,
  }


```

---

```rust

  Item {
    name: "Wood",
    description: "Useful for crafting",
    value: Stats {
        health: 0.0,
        food: 0.0,
        water: 0.0,
        energy: 0.0,
    },
    uses_until_breakdown: 0,
    consumable: false,
    risk: 0.0,
  },


```

---

<img src="https://media.giphy.com/media/JuJKazEn6dF7i/giphy.gif" alt="man eating wood frame" />

---

## 🤔

<ul>
  <li class="fragment">Different structs?</li>
  <li class="fragment">Traits?</li>
  <li class="fragment">🤯</li>
</ul>

---

### Enums

```rust

  enum ItemProperties {
      StandardItem,
      ConsumeableItem {
          value: ItemStats,
          risk: f64,
      },
      ToolItem {
          uses_until_breakdown: i32,
      },
  }


```

---

### Struct with enumerable property

```rust

  struct Item {
      name: &'static str,
      description: &'static str,
      properties: ItemProperties,
  }


```

---

### Methods

```rust

  impl Item {
      pub fn decrease_use(&mut self) -> bool {
          // ...
      }
  }


```

---

```rust

  Item {
    name: "Wood",
    description: "Useful for crafting",
    properties: ItemProperties::StandardItem,
  }


```

---

<img src="./public/statue.jpeg" style="max-height:75vh" alt="statue">

