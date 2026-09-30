# Implementation Plan — TaskFlow

Karena tujuan lu **belajar**, implementasinya jangan dibuat seperti proyek profesional yang langsung jadi. Kita bikin **step-by-step**, dan setiap tahap punya konsep yang harus lu pahami sebelum lanjut.

---

## 1. Tech Stack

### Versi Vue

* Vue 3
* Vite
* JavaScript
* Tailwind CSS
* Vue Router
* Pinia
* Firebase

### Versi React

* React
* Vite
* JavaScript
* Tailwind CSS
* React Router
* Zustand
* Firebase

### Backend

Satu Firebase project bisa digunakan oleh kedua versi.

```text
                Firebase
                   │
          ┌────────┴────────┐
          │                 │
      TaskFlow Vue      TaskFlow React
          │                 │
       Pinia              Zustand
```

Jadi lu tidak perlu membuat dua database.

---

## 2. Urutan Pengerjaan

Jangan mengerjakan Vue dan React secara bersamaan.

Urutannya:

```text
JavaScript Fundamental
        ↓
TaskFlow Vue
        ↓
TaskFlow Vue + Firebase
        ↓
TaskFlow React
        ↓
TaskFlow React + Firebase
        ↓
Perbandingan Vue vs React
```

**Vue diselesaikan dulu**, baru React.

Alasannya supaya saat masuk React lu sudah memahami masalah yang ingin diselesaikan. Jadi lu tidak belajar dua syntax sekaligus.

---

## 3. Phase 0 — Persiapan

### Tujuan

Menyiapkan environment.

### Install

```text
Node.js
VS Code
Git
```

Cek:

```bash
node -v
npm -v
git --version
```

### Buat repository

```text
taskflow-learning
```

Struktur:

```text
taskflow-learning/
│
├── vue/
│
└── react/
```

---

## 4. Phase 1 — JavaScript Fundamental

Sebelum masuk framework, buat latihan kecil terlebih dahulu.

### Materi

Pelajari:

```text
variable
let / const

data type
string
number
boolean

array
object

function

if / else

for
map
filter
find

destructuring

spread operator

template literal

import / export

Promise

async / await
```

### Mini latihan

Buat data:

```js
const tasks = [
  {
    id: 1,
    title: "Belajar Vue",
    completed: false,
  },
  {
    id: 2,
    title: "Belajar React",
    completed: true,
  },
];
```

Lalu latihan:

```text
Tampilkan semua task
Cari task berdasarkan ID
Filter task yang selesai
Filter task yang belum selesai
Tambah task
Edit task
Hapus task
```

**Checkpoint:** jangan lanjut sebelum lu cukup nyaman membaca kode JavaScript tersebut.

---

## 5. Phase 2 — Membuat Project Vue

Buat project:

```bash
npm create vite@latest vue -- --template vue
```

Kemudian:

```bash
cd vue
npm install
npm run dev
```

### Pelajari struktur

```text
vue/
├── src/
│   ├── assets/
│   ├── components/
│   ├── App.vue
│   └── main.js
│
├── public/
├── package.json
└── vite.config.js
```

Jangan langsung membuat semua folder.

---

## 6. Phase 3 — Vue Basic Playground

Sebelum TaskFlow, gunakan `App.vue` sebagai playground.

### Latihan 1 — Interpolation

```text
Halo {{ name }}
```

Pelajari:

```text
{{ }}
```

### Latihan 2 — State

Pelajari:

```text
ref()
```

Buat counter:

```text
Count: 0

[-] [+]
```

### Latihan 3 — Event

Pelajari:

```text
@click
```

### Latihan 4 — Conditional

Pelajari:

```text
v-if
v-else
v-show
```

### Latihan 5 — Loop

Pelajari:

```text
v-for
```

### Latihan 6 — Form

Pelajari:

```text
v-model
```

Buat:

```text
Nama:
[Davin]

Halo Davin
```

---

## 7. Phase 4 — TaskFlow Vue Basic

Sekarang mulai project sebenarnya.

Buat:

```text
src/
├── components/
│   └── TaskCard.vue
│
├── views/
│   └── Dashboard.vue
│
├── data/
│   └── tasks.js
│
├── App.vue
└── main.js
```

### TaskCard

Tugasnya hanya menampilkan:

```text
Title
Description
Status
```

### Dashboard

Menampilkan:

```text
TaskCard
TaskCard
TaskCard
```

Gunakan:

```text
v-for
```

---

## 8. Phase 5 — Props

Sekarang TaskCard jangan memiliki data sendiri.

Dashboard mengirim data:

```text
Dashboard
     │
     │ props
     ↓
TaskCard
```

Pelajari:

```text
props
```

Contoh konsep:

```text
TaskCard menerima task
```

---

## 9. Phase 6 — Emit

Tambahkan tombol:

```text
✓ Complete
🗑 Delete
```

TaskCard mengirim event:

```text
TaskCard
   │
   │ emit
   ↓
Dashboard
```

Pelajari:

```text
emit
```

Di sini lu sudah belajar konsep penting:

```text
Parent
 ↓ props
Child

Child
 ↓ emit
Parent
```

---

## 10. Phase 7 — Task CRUD

Implementasikan:

### Create

```text
Tambah Task
```

### Read

```text
Daftar Task
```

### Update

```text
Edit Task
```

### Delete

```text
Hapus Task
```

Belum menggunakan Firebase.

Data masih:

```text
JavaScript
 ↓
Vue state
```

---

## 11. Phase 8 — Form Component

Buat:

```text
components/
└── TaskForm.vue
```

Form:

```text
Title
Description
Priority
Category
Deadline
```

Pelajari:

```text
v-model
form submit
validation
reset form
```

---

## 12. Phase 9 — Computed

Sekarang buat statistik:

```text
Total       10
Pending      6
Completed    4
```

Pelajari:

```text
computed()
```

Kemudian buat:

```text
filteredTasks
completedTasks
pendingTasks
```

---

## 13. Phase 10 — Search & Filter

Tambahkan:

```text
┌─────────────────────────────┐
│ 🔍 Search task              │
└─────────────────────────────┘

[ Semua ] [ Pending ] [ Selesai ]
```

Filter berdasarkan:

```text
Title
Status
Priority
Category
```

Gunakan `computed()` untuk hasil filter.

---

## 14. Phase 11 — Vue Router

Install:

```bash
npm install vue-router
```

Buat:

```text
views/
├── Dashboard.vue
├── TaskDetail.vue
├── CreateTask.vue
└── EditTask.vue
```

Routing:

```text
/
/tasks/:id
/tasks/create
/tasks/:id/edit
```

Pelajari:

```text
Router
Route
RouterLink
useRoute()
useRouter()
```

---

## 15. Phase 12 — Pinia

Install:

```bash
npm install pinia
```

Buat:

```text
stores/
└── taskStore.js
```

Arsitektur:

```text
             Pinia
               │
       ┌───────┼────────┐
       ↓       ↓        ↓
 Dashboard  Detail    Form
```

Pindahkan data task dari component ke Pinia.

Pelajari:

```text
state
getters
actions
```

---

## 16. Phase 13 — Local Storage

Sebelum Firebase, buat data tetap tersimpan setelah browser direfresh.

```text
Vue
 ↓
Pinia
 ↓
localStorage
```

Pelajari:

```text
localStorage.setItem()
localStorage.getItem()
JSON.stringify()
JSON.parse()
```

**Checkpoint:** tutup browser → buka lagi → task masih ada.

---

## 17. Phase 14 — Firebase

Sekarang baru masuk backend.

Install:

```bash
npm install firebase
```

Buat:

```text
src/
├── firebase/
│   └── config.js
│
└── services/
    └── taskService.js
```

Arsitektur:

```text
Vue
 ↓
Pinia
 ↓
taskService
 ↓
Firestore
```

---

## 18. Phase 15 — Firestore CRUD

Buat collection:

```text
tasks
```

Document:

```text
tasks/
   taskId
      title
      description
      priority
      category
      deadline
      completed
      createdAt
```

Implementasikan:

```text
Create → Firestore
Read   → Firestore
Update → Firestore
Delete → Firestore
```

Setelah berhasil:

```text
localStorage
```

tidak lagi menjadi sumber utama.

---

## 19. Phase 16 — Firebase Authentication

Ini **jangan dikerjakan di awal**.

Tambahkan:

```text
Login
Register
Logout
```

Setiap task mempunyai:

```text
userId
```

Sehingga:

```text
User A
 ├── Task 1
 ├── Task 2
 └── Task 3

User B
 ├── Task 4
 └── Task 5
```

---

## 20. Phase 17 — TaskFlow Vue Selesai

Pada titik ini versi Vue sudah:

```text
Vue 3
├── Components
├── Props
├── Emit
├── ref
├── reactive
├── computed
├── watch
├── Forms
├── CRUD
├── Router
├── Pinia
├── Local Storage
└── Firebase
```

**Baru setelah ini pindah ke React.**

---

## 21. Phase 18 — Buat TaskFlow React

Buat project kedua:

```bash
npm create vite@latest react -- --template react
```

Install:

```bash
npm install
```

Gunakan desain dan requirement **yang sama persis**.

Jangan menambah fitur baru.

Tujuannya:

> "Bagaimana cara membuat aplikasi yang sama menggunakan React?"

---

## 22. Phase 19 — React Basic

Gunakan `App.jsx` sebagai playground.

Pelajari:

```text
JSX
Component
props
useState
event
conditional rendering
array.map()
forms
```

Contoh latihan:

```text
Counter
 ↓
Todo List
 ↓
Task Card
 ↓
Task Form
```

---

## 23. Phase 20 — React Component

Struktur:

```text
src/
├── components/
│   ├── TaskCard.jsx
│   ├── TaskList.jsx
│   ├── TaskForm.jsx
│   ├── TaskStats.jsx
│   └── TaskFilter.jsx
│
├── pages/
│   ├── Dashboard.jsx
│   ├── TaskDetail.jsx
│   ├── CreateTask.jsx
│   └── EditTask.jsx
│
└── App.jsx
```

---

## 24. Phase 21 — React State

Gunakan:

```text
useState()
```

Untuk:

```text
tasks
search
filter
form
```

Bandingkan dengan Vue:

```text
Vue                 React

ref()          ↔    useState()
@click         ↔    onClick
v-for          ↔    map()
v-if           ↔    condition
v-model        ↔    value + onChange
```

---

## 25. Phase 22 — React useEffect

Pelajari:

```text
useEffect()
```

Gunakan untuk:

```text
localStorage
fetch data
side effect
```

Di tahap ini lu bisa membandingkan:

```text
Vue watch()
       ↕
React useEffect()
```

**Tapi jangan menganggap keduanya 100% sama.** Ini justru bagian yang perlu lu pahami.

---

## 26. Phase 23 — React Router

Install:

```bash
npm install react-router-dom
```

Buat route yang sama:

```text
/
/tasks/:id
/tasks/create
/tasks/:id/edit
```

---

## 27. Phase 24 — State Management React

Gunakan Zustand agar konsepnya gampang dipelajari.

```bash
npm install zustand
```

Struktur:

```text
stores/
└── taskStore.js
```

Bandingkan:

```text
Vue                  React

Pinia          ↔     Zustand
state          ↔     state
getters        ↔     derived data
actions        ↔     actions
```

---

## 28. Phase 25 — Firebase React

Gunakan Firebase project yang sama.

```text
TaskFlow Vue ──────┐
                   ├── Firebase
TaskFlow React ────┘
```

Implementasikan:

```text
Authentication
Firestore
CRUD
```

---

## 29. Phase 26 — Final Comparison

Setelah kedua aplikasi selesai, buat dokumentasi:

```text
TaskFlow Vue vs TaskFlow React
```

Bandingkan:

```text
Project structure
Component
State
Props
Event
Form
Computed
Watch / Effect
Routing
State management
Firebase
```

Contoh:

| Konsep        | Vue          | React            |
| ------------- | ------------ | ---------------- |
| State         | `ref()`      | `useState()`     |
| Component     | `.vue`       | `.jsx`           |
| Loop          | `v-for`      | `.map()`         |
| Conditional   | `v-if`       | JSX condition    |
| Event         | `@click`     | `onClick`        |
| Form          | `v-model`    | controlled input |
| Derived state | `computed()` | derived state    |
| Side effect   | `watch()`    | `useEffect()`    |
| Global state  | Pinia        | Zustand          |
| Router        | Vue Router   | React Router     |

---

## 30. Struktur Final Repository

Pada akhirnya:

```text
taskflow-learning/
│
├── README.md
│
├── vue/
│   ├── src/
│   │   ├── components/
│   │   ├── views/
│   │   ├── stores/
│   │   ├── services/
│   │   ├── composables/
│   │   └── firebase/
│   │
│   └── package.json
│
├── react/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── stores/
│   │   ├── services/
│   │   └── firebase/
│   │
│   └── package.json
│
└── documentation/
    ├── vue-notes.md
    ├── react-notes.md
    └── vue-vs-react.md
```

---

## Aturan belajar yang gw sarankan

Yang paling penting: **jangan minta AI langsung membuat seluruh aplikasinya.**

Pakai pola:

```text
1. Pelajari konsep
       ↓
2. Coba sendiri
       ↓
3. Ketemu error
       ↓
4. Tanya AI
       ↓
5. Pahami kenapa error
       ↓
6. Perbaiki sendiri
       ↓
7. Lanjut fitur berikutnya
```

Misalnya lu sedang belajar `props`, jangan langsung minta:

> "Buatkan TaskCard Vue."

Lebih bagus:

> "Gw sedang belajar props di Vue. Jelaskan konsepnya dan kasih latihan kecil, jangan kasih full code."

Setelah lu paham baru implementasikan ke TaskFlow.

Dengan cara ini, **TaskFlow bukan cuma project portfolio**, tapi benar-benar menjadi project latihan yang membawa lu dari **JavaScript → Vue → React → Firebase** secara bertahap.
