# Lerning rust

# การติดตั้งและเริ่มต้นภาษา Rust 🦀

---

## ขั้นตอนที่ 1: ติดตั้ง Rust

วิธีที่แนะนำที่สุดคือใช้ **rustup** (ตัวจัดการเวอร์ชัน Rust)

**Linux / macOS:**
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

**Windows:**
ดาวน์โหลด installer จาก https://rustup.rs แล้วรันไฟล์ `.exe`

หลังติดตั้งเสร็จ ให้รีสตาร์ท terminal แล้วตรวจสอบ:
```bash
rustc --version
cargo --version
```

---

## ขั้นตอนที่ 2: สร้างโปรเจกต์แรก

```bash
cargo new hello_rust
cd hello_rust
```

โครงสร้างโฟลเดอร์ที่ได้:
```
hello_rust/
├── Cargo.toml   ← ไฟล์ config โปรเจกต์
└── src/
    └── main.rs  ← โค้ดหลัก
```

---

## ขั้นตอนที่ 3: Hello World

ไฟล์ `src/main.rs`:
```rust
fn main() {
    println!("Hello, World!");
}
```

รันโปรแกรม:
```bash
cargo run
```

---

## ขั้นตอนที่ 4: ตัวอย่างพื้นฐาน

### 📌 ตัวแปรและชนิดข้อมูล
```rust
fn main() {
    let x = 5;           // immutable (เปลี่ยนค่าไม่ได้)
    let mut y = 10;      // mutable (เปลี่ยนค่าได้)
    y = 20;

    let name: &str = "Rust";
    let pi: f64 = 3.14;
    let is_cool: bool = true;

    println!("x={}, y={}, name={}, pi={}, cool={}", x, y, name, pi, is_cool);
}
```

---

### 📌 If / Else
```rust
fn main() {
    let score = 85;

    if score >= 80 {
        println!("เกรด A");
    } else if score >= 70 {
        println!("เกรด B");
    } else {
        println!("เกรด C");
    }
}
```

---

### 📌 Loop และ For
```rust
fn main() {
    // for loop
    for i in 1..=5 {
        println!("ครั้งที่ {}", i);
    }

    // while loop
    let mut count = 0;
    while count < 3 {
        println!("count = {}", count);
        count += 1;
    }
}
```

---

### 📌 Function (ฟังก์ชัน)
```rust
fn add(a: i32, b: i32) -> i32 {
    a + b  // ไม่ต้องมี return (บรรทัดสุดท้ายคือค่าที่ return)
}

fn greet(name: &str) {
    println!("สวัสดี, {}!", name);
}

fn main() {
    let result = add(3, 7);
    println!("3 + 7 = {}", result);
    greet("ภาษา Rust");
}
```

---

### 📌 Vec (Array แบบ dynamic)
```rust
fn main() {
    let mut fruits = vec!["แอปเปิ้ล", "กล้วย", "ส้ม"];
    fruits.push("มะม่วง");

    for fruit in &fruits {
        println!("{}", fruit);
    }

    println!("จำนวน: {}", fruits.len());
}
```

---

### 📌 Struct (โครงสร้างข้อมูล)
```rust
struct Person {
    name: String,
    age: u32,
}

impl Person {
    fn greet(&self) {
        println!("สวัสดี ฉันชื่อ {} อายุ {} ปี", self.name, self.age);
    }
}

fn main() {
    let p = Person {
        name: String::from("สมชาย"),
        age: 25,
    };
    p.greet();
}
```

---

### 📌 Pattern Matching (match)
```rust
fn main() {
    let day = 3;

    let day_name = match day {
        1 => "จันทร์",
        2 => "อังคาร",
        3 => "พุธ",
        4 => "พฤหัส",
        5 => "ศุกร์",
        _ => "วันหยุด",  // _ คือ default
    };

    println!("วัน{}", day_name);
}
```

---

## สรุปคำสั่ง Cargo ที่ใช้บ่อย

| คำสั่ง | ความหมาย |
|--------|----------|
| `cargo new <ชื่อ>` | สร้างโปรเจกต์ใหม่ |
| `cargo run` | คอมไพล์และรัน |
| `cargo build` | คอมไพล์อย่างเดียว |
| `cargo build --release` | คอมไพล์แบบ optimized |
| `cargo check` | ตรวจ error โดยไม่คอมไพล์ |
| `cargo test` | รัน unit tests |
