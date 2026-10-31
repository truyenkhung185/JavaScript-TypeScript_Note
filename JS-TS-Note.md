# 📘 Ghi Chú JS và TS

> Bản tóm tắt cô đọng, chuyên sâu và có tính ứng dụng cao dành cho lập trình viên từ căn bản đến nâng cao. Được thiết kế theo góc nhìn thực chiến, giải quyết triệt để sự khác biệt cốt lõi giữa JavaScript Runtime và TypeScript Compiler, các bẫy phổ biến và best practices hiện đại.

---

## 🧭 Mục lục tổng quan

- [Phần 1: Nền tảng JavaScript Runtime & Hệ thống Kiểu TypeScript](#phần-1-nền-tảng-javascript-runtime--hệ-thống-kiểu-typescript)
  - [1.1 Tư duy: Static Types vs Dynamic Runtime](#11-tư-duy-static-types-vs-dynamic-runtime)
  - [1.2 Các kiểu nguyên thủy (Primitives), Coercion và Strict Equality](#12-các-kiểu-nguyên-thủy-primitives-coercion-và-strict-equality)
  - [1.3 Nullability: null vs undefined, Nullish Coalescing (??) & Optional Chaining (?.)](#13-nullability-null-vs-undefined-nullish-coalescing---optional-chaining-)
  - [1.4 Phạm vi biến (Scope) & Bộ nhớ: var, let, const, Temporal Dead Zone (TDZ)](#14-phạm-vi-biến-scope--bộ-nhớ-var-let-const-temporal-dead-zone-tdz)
  - [1.5 Chiến lược gõ kiểu TS: any vs unknown vs never vs void](#15-chiến-lược-gõ-kiểu-ts-any-vs-unknown-vs-never-vs-void)
- [Phần 2: Cấu trúc Dữ liệu & Toán tử Hiện Đại](#phần-2-cấu-trúc-dữ-liệu--toán-tử-hiện-đại)
  - [2.1 Array Mutations vs Immutability, Tuples, `as const`](#21-array-mutations-vs-immutability-tuples-as-const)
  - [2.2 Object Shape: Type Alias vs Interface (Khi nào dùng cái nào?)](#22-object-shape-type-alias-vs-interface-khi-nào-dùng-cái-nào)
  - [2.3 Set, Map, WeakMap, WeakSet & Symbol](#23-set-map-weakmap-weakset--symbol)
  - [2.4 Destructuring, Rest/Spread & Shallow vs Deep Clone](#24-destructuring-restspread--shallow-vs-deep-clone)
- [Phần 3: Hàm (Functions) & Mô hình Thực thi](#phần-3-hàm-functions--mô-hình-thực-thi)
  - [3.1 Function Declarations vs Expressions vs Arrow Functions](#31-function-declarations-vs-expressions-vs-arrow-functions)
  - [3.2 Cơ chế `this`, Call / Apply / Bind](#32-cơ-chế-this-call--apply--bind)
  - [3.3 Function Signatures, Overloads & Currying](#33-function-signatures-overloads--currying)
- [Phần 4: Lập trình Hướng đối tượng (OOP) & Prototype](#phần-4-lập-trình-hướng-đối-tượng-oop--prototype)
  - [4.1 Prototype Chain vs ES6+ Class](#41-prototype-chain-vs-es6-class)
  - [4.2 Access Modifiers (TS `private` vs JS `#private field`)](#42-access-modifiers-ts-private-vs-js-private-field)
  - [4.3 Abstract Classes vs Interfaces](#43-abstract-classes-vs-interfaces)
- [Phần 5: Thu Hẹp Kiểu (Type Narrowing) & Phòng Thủ Runtime](#phần-5-thu-hẹp-kiểu-type-narrowing--phòng-thủ-runtime)
  - [5.1 Control Flow Analysis & Type Guards tự nhiên (`typeof`, `instanceof`, `in`)](#51-control-flow-analysis--type-guards-tự-nhiên-typeof-instanceof-in)
  - [5.2 Custom Type Predicates (`val is Type`) & Assertion Functions (`asserts val`)](#52-custom-type-predicates-val-is-type--assertion-functions-asserts-val)
  - [5.3 Discriminated Unions & Exhaustive Checking với `never`](#53-discriminated-unions--exhaustive-checking-với-never)
- [Phần 6: Generic Programming & Hệ Thống Kiểu Nâng Cao](#phần-6-generic-programming--hệ-thống-kiểu-nâng-cao)
  - [6.1 Generics căn bản & Constraints (`extends`)](#61-generics-căn-bản--constraints-extends)
  - [6.2 Keyof, Indexed Access (`T[K]`) & Lookup Types](#62-keyof-indexed-access-tk--lookup-types)
  - [6.3 Mapped Types & Key Remapping (`as`)](#63-mapped-types--key-remapping-as)
  - [6.4 Conditional Types & Từ khóa `infer`](#64-conditional-types--từ-khóa-infer)
  - [6.5 Template Literal Types thực chiến](#65-template-literal-types-thực-chiến)
  - [6.6 Bảng tra cứu Utility Types có sẵn & Cách tự viết lại](#66-bảng-tra-cứu-utility-types-có-sẵn--cách-tự-viết-lại)
- [Phần 7: Bất đồng bộ (Asynchronous) & Luồng Sự Kiện (Event Loop)](#phần-7-bất-đồng-bộ-asynchronous--luồng-sự-kiện-event-loop)
  - [7.1 Bản chất Event Loop: Call Stack, Web APIs, Microtask vs Macrotask](#71-bản-chất-event-loop-call-stack-web-apis-microtask-vs-macrotask)
  - [7.2 Vòng đời Promise & Async/Await](#72-vòng-đời-promise--asyncawait)
  - [7.3 Promise Concurrency: All, AllSettled, Race, Any](#73-promise-concurrency-all-allsettled-race-any)
  - [7.4 Iterators, Generators & Async Iterables](#74-iterators-generators--async-iterables)
- [Phần 8: Cấu hình Dự án & Thiết lập Tooling Chuẩn Enterprise](#phần-8-cấu-hình-dự-án--thiết-lập-tooling-chuẩn-enterprise)
  - [8.1 Giải mã các cờ cốt lõi trong `tsconfig.json`](#81-giải-mã-các-cờ-cốt-lõi-trong-tsconfigjson)
  - [8.2 Module Resolution: CommonJS vs ESM (NodeNext)](#82-module-resolution-commonjs-vs-esm-nodenext)
  - [8.3 Ambient Declarations (`.d.ts`) & Module Augmentation](#83-ambient-declarations-dts--module-augmentation)
- [Phần 9: Tổng hợp Lỗi Thường Gặp & Best Practices Checklist](#phần-9-tổng-hợp-lỗi-thường-gặp--best-practices-checklist)

---

# Phần 1: Nền tảng JavaScript Runtime & Hệ thống Kiểu TypeScript

## 1.1 Tư duy: Static Types vs Dynamic Runtime

Một trong những sai lầm lớn nhất của người mới học là **nhầm lẫn giữa TypeScript compiler và JavaScript runtime**:

- **TypeScript Type System chỉ tồn tại ở giai đoạn compile-time (biên dịch)**. Khi chạy `tsc`, toàn bộ type annotations, interfaces, type aliases và type assertions sẽ bị xóa sạch (*type erasure*), chỉ còn lại JavaScript thuần.
- **Không có kiểm tra kiểu tự động ở Runtime**: TypeScript không thể bảo vệ bạn trước dữ liệu trả về từ API, payload người dùng nhập hay `JSON.parse()`. Để an toàn ở runtime, bạn phải dùng type guard hoặc thư viện schema validation (Zod, Valibot).

```typescript
interface User {
  id: string;
  age: number;
}

const raw = JSON.parse('{"id": "1", "age": "twenty"}') as User;
raw.age.toFixed(0);
```

---

## 1.2 Các kiểu nguyên thủy (Primitives), Coercion và Strict Equality

JavaScript có 7 kiểu nguyên thủy: `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, và `bigint`.

### Type Coercion (Ép kiểu ngầm) & Toán tử So sánh
Tránh hoàn toàn toán tử `==` vì bảng chân trị phức tạp và dễ gây lỗi tiềm ẩn. Luôn dùng `===` (Strict equality: kiểm tra cả giá trị lẫn kiểu).

```javascript
[] + [];
[] + {};
true + true;
"5" - 3;
"5" + 3;

0 === false;
null === undefined;
```

---

## 1.3 Nullability: null vs undefined, Nullish Coalescing (??) & Optional Chaining (?.)

- `undefined`: Biến đã được khai báo nhưng chưa được gán giá trị, hoặc thuộc tính không tồn tại trong object.
- `null`: Giá trị có chủ đích, thể hiện rằng "không có gì cả" / rỗng.

### Phân biệt `??` (Nullish Coalescing) và `||` (Logical OR)
Toán tử `||` trả về vế phải nếu vế trái là bất kỳ giá trị *falsy* nào (`0`, `""`, `false`, `NaN`, `null`, `undefined`). Toán tử `??` chỉ trả về vế phải khi vế trái thực sự là `null` hoặc `undefined`.

```typescript
interface AppSettings {
  port?: number;
  verbose?: boolean;
}

function initServer(config: AppSettings) {
  const portA = config.port || 3000;
  const portB = config.port ?? 3000;
  const isDebug = config?.verbose ?? false;
}
```

---

## 1.4 Phạm vi biến (Scope) & Bộ nhớ: var, let, const, Temporal Dead Zone (TDZ)

| Tiêu chí | `var` | `let` | `const` |
| :--- | :--- | :--- | :--- |
| **Phạm vi (Scope)** | Function Scope | Block Scope (`{}`) | Block Scope (`{}`) |
| **Hoisting** | Hoist & gán `undefined` | Hoist nhưng nằm trong TDZ | Hoist nhưng nằm trong TDZ |
| **Gán lại (Reassign)** | Có | Có | Không |
| **Khai báo lại trong scope** | Có | Không | Không |

> **Temporal Dead Zone (TDZ)**: Là khoảng thời gian từ khi bắt đầu khối lệnh cho đến khi câu lệnh khai báo biến `let`/`const` được thực thi. Truy cập biến trong TDZ sẽ gây lỗi `ReferenceError`.

```javascript
{
  let myVar = 42;
  console.log(myVar);
}
```

---

## 1.5 Chiến lược gõ kiểu TS: any vs unknown vs never vs void

```
             ┌───────────┐
             │    any    │
             └───────────┘
                   │
             ┌───────────┐
             │  unknown  │
             └───────────┘
                   │
      ┌────────────┴────────────┐
      ▼                         ▼
Các kiểu cụ thể (string, number, object, ...)
      ▲                         ▲
      └────────────┬────────────┘
                   │
             ┌───────────┐
             │   never   │
             └───────────┘
```

### So sánh chi tiết

1. **`any`**: Tắt hoàn toàn kiểm tra kiểu của TypeScript. Sử dụng `any` làm mất ý nghĩa của TypeScript.
2. **`unknown`**: Nhận mọi kiểu dữ liệu nhưng **bắt buộc phải kiểm tra (narrowing)** trước khi gọi hàm hoặc truy cập thuộc tính. Thích hợp cho API response, user input.
3. **`void`**: Hàm chạy xong và không trả về giá trị hữu ích (ở runtime thực chất trả `undefined`).
4. **`never`**: Hàm không bao giờ kết thúc (ném exception liên tục, vòng lặp vô hạn `while(true)`), hoặc một trạng thái logic không thể chạm tới.

```typescript
function processExternalData(data: unknown) {
  if (typeof data === "string") {
    console.log(data.trim());
  }
}

function panic(message: string): never {
  throw new Error(`Fatal: ${message}`);
}
```

---

# Phần 2: Cấu trúc Dữ liệu & Toán tử Hiện Đại

## 2.1 Array Mutations vs Immutability, Tuples, `as const`

### Phương thức mảng: Đổi mảng gốc (Mutate) vs Tạo mảng mới (Immutable)
- **Mutating methods**: `push()`, `pop()`, `shift()`, `unshift()`, `splice()`, `reverse()`, `sort()`.
- **Immutable methods**: `map()`, `filter()`, `reduce()`, `slice()`, `concat()`, và các hàm ES2023 mới: `toSorted()`, `toReversed()`, `toSpliced()`.

```typescript
const numbers = [3, 1, 4, 1, 5];
const sorted = numbers.toSorted((a, b) => a - b);
console.log(numbers);
console.log(sorted);
```

### Tuples và `as const` (Const Assertions)
`as const` biến toàn bộ object/mảng thành giá trị literal không thể sửa đổi (`readonly`) ở cấp độ sâu nhất (*deep readonly*).

```typescript
const routes = ["/home", "/about", "/contact"];

const CONFIG = {
  apiEndpoint: "https://api.domain.com",
  timeout: 5000,
  roles: ["ADMIN", "MEMBER"] as const
} as const;

type UserRole = typeof CONFIG.roles[number];
```

---

## 2.2 Object Shape: Type Alias vs Interface (Khi nào dùng cái nào?)

Cả hai đều định nghĩa hình dạng (shape) của object, nhưng có các điểm khác biệt then chốt:

| Tiêu chí | `interface` | `type` |
| :--- | :--- | :--- |
| **Mục đích chính** | Hướng đối tượng, API public của thư viện | Mô tả cấu trúc dữ liệu, union, primitives, tuples |
| **Declaration Merging** | Có (tự động gộp các interface trùng tên) | Không (báo lỗi trùng tên) |
| **Kế thừa cú pháp** | `interface B extends A` | `type B = A & { ... }` (Intersection) |
| **Tạo Union / Mapped Type** | Không thể trực tiếp | Được hỗ trợ đầy đủ |
| **Hiệu năng TypeScript Compiler**| Nhanh hơn khi check kế thừa phân cấp | Đôi khi chậm hơn nếu lồng nhiều Intersection phức tạp |

### Declaration Merging (Tính năng độc quyền của Interface)
Rất hữu ích khi mở rộng type của thư viện bên ngoài (ví dụ thêm thuộc tính vào `Window` hoặc `ProcessEnv`).

```typescript
interface CartItem {
  id: string;
  price: number;
}

interface CartItem {
  quantity: number;
}

const item: CartItem = { id: "p1", price: 100, quantity: 2 };
```

---

## 2.3 Set, Map, WeakMap, WeakSet & Symbol

- **`Map`**: Cấu trúc Key-Value linh hoạt, chấp nhận **mọi kiểu dữ liệu** làm key (kể cả object/hàm), giữ nguyên thứ tự chèn, có thuộc tính `.size`.
- **`Set`**: Tập hợp các phần tử **duy nhất** (unique), loại bỏ duplicate tức thì.
- **`WeakMap` / `WeakSet`**: Chỉ chấp nhận Key là **Object**. Không ngăn cản Garbage Collector dọn dẹp object đó khỏi bộ nhớ nếu không còn biến nào tham chiếu tới nó. Không duyệt qua được (`not iterable`), không có thuộc tính `.size`. Cực kỳ hữu dụng để lưu private cache hoặc metadata tránh rò rỉ bộ nhớ (memory leak).
- **`Symbol`**: Kiểu nguyên thủy đảm bảo tính duy nhất tuyệt đối. Thường dùng làm key ẩn cho object, tránh đụng độ tên thuộc tính giữa các thư viện.

```typescript
const metaCache = new WeakMap<object, { lastAccess: number }>();

let userEntity: { name: string } | null = { name: "Hải" };
metaCache.set(userEntity, { lastAccess: Date.now() });

userEntity = null;
```

---

## 2.4 Destructuring, Rest/Spread & Shallow vs Deep Clone

### Shallow Clone (Bản sao nông)
Toán tử spread `{ ...obj }` hoặc `Object.assign({}, obj)` chỉ sao chép các thuộc tính ở tầng 1. Các object con bên trong vẫn giữ nguyên tham chiếu cũ!

### Deep Clone chuẩn hiện đại với `structuredClone`
Từ Node 17+ và trình duyệt hiện đại, không cần dùng thư viện ngoài (`lodash.cloneDeep`) hay trò hack lỗi thời `JSON.parse(JSON.stringify(obj))` (vốn làm mất `Date`, `Map`, `Set`, `undefined`, và văng lỗi khi có tham chiếu vòng circular reference).

```typescript
const original = {
  name: "Bình",
  createdAt: new Date(),
  scores: [10, 9, 8],
  metadata: { verified: true }
};

const deepCopy = structuredClone(original);
deepCopy.metadata.verified = false;

console.log(original.metadata.verified);
console.log(deepCopy.createdAt instanceof Date);
```

---

# Phần 3: Hàm (Functions) & Mô hình Thực thi

## 3.1 Function Declarations vs Expressions vs Arrow Functions

```javascript
function calculateTotal(a, b) {
  return a + b;
}

const calculateDiff = function(a, b) {
  return a - b;
};

const multiply = (a, b) => a * b;
```

---

## 3.2 Cơ chế `this`, Call / Apply / Bind

Từ khóa `this` trong JavaScript **phụ thuộc vào cách hàm được gọi** (*Call-site*), ngoại trừ Arrow Function (lấy `this` theo ngữ cảnh bao quanh nó - *Lexical scoping*).

```javascript
const agent = {
  name: "Omega",
  greet() {
    console.log(`Tôi là ${this.name}`);
  },
  delayedGreet() {
    setTimeout(() => {
      console.log(`Delayed: Tôi là ${this.name}`);
    }, 100);
  }
};

const boundGreet = agent.greet.bind(agent);
boundGreet();
```

---

## 3.3 Function Signatures, Overloads & Currying

TypeScript cho phép định nghĩa **Function Overloads** để cung cấp nhiều kiểu tham số / kết quả trả về khác nhau trên cùng một tên hàm logic.

```typescript
function parseInput(input: string): string[];
function parseInput(input: number): number[];
function parseInput(input: string | number): (string | number)[] {
  if (typeof input === "string") {
    return input.split("");
  }
  return [input];
}

const resStr = parseInput("hello");
const resNum = parseInput(100);
```

---

# Phần 4: Lập trình Hướng đối tượng (OOP) & Prototype

## 4.1 Prototype Chain vs ES6+ Class

Dưới nền tảng của JavaScript, **không có class thực sự**. Class chỉ là lớp vỏ cú pháp (*syntactic sugar*) phủ lên hệ thống Prototype Delegation.

```javascript
function Animal(name) {
  this.name = name;
}
Animal.prototype.speak = function() {
  return `${this.name} phát ra âm thanh.`;
};

const dog = new Animal("Cún");
```

---

## 4.2 Access Modifiers (TS `private` vs JS `#private field`)

Đây là điểm cực kỳ hay bị nhầm lẫn giữa bảo vệ ở Compile-time và Bảo mật thực tế ở Runtime:

| Đặc tính | TypeScript `private` | JavaScript ECMAScript `#field` |
| :--- | :--- | :--- |
| **Thời điểm hiệu lực** | Chỉ ở Compile-time | Ở cả Runtime lẫn Compile-time |
| **Runtime Output** | Compile ra thuộc tính bình thường (vẫn truy cập được qua `obj["field"]`) | Bị khóa cứng ở cấp độ VM, gọi lén sẽ văng SyntaxError |
| **Hiệu năng & Ký hiệu** | `private token: string` | `#token: string` |

```typescript
class Vault {
  private softSecret = "ts-private";
  #hardSecret = "js-runtime-private";

  unlock() {
    return this.#hardSecret;
  }
}

const v = new Vault();
```

---

## 4.3 Abstract Classes vs Interfaces

- **Interface**: Hoàn toàn biến mất khi build. Không chứa logic thực thi hay method body. Hỗ trợ đa kế thừa (`class C implements A, B`).
- **Abstract Class**: Tồn tại ở runtime dưới dạng constructor function / class. Có thể chứa logic chia sẻ chung (*shared implementation*), template methods, và buộc lớp con phải implement các abstract methods.

```typescript
abstract class BaseRepository<T> {
  log(action: string) {
    console.log(`[AUDIT] Action: ${action} at ${new Date().toISOString()}`);
  }

  abstract findById(id: string): Promise<T | null>;
}
```

---

# Phần 5: Thu Hẹp Kiểu (Type Narrowing) & Phòng Thủ Runtime

## 5.1 Control Flow Analysis & Type Guards tự nhiên

TypeScript phân tích luồng code để thu hẹp kiểu biến thông qua các điều kiện rẽ nhánh:

```typescript
function processValue(val: string | number | Date | { [key: string]: any }) {
  if (typeof val === "string") {
    return val.toUpperCase();
  }
  if (typeof val === "number") {
    return val.toFixed(2);
  }
  if (val instanceof Date) {
    return val.getFullYear();
  }
  if ("customProperty" in val) {
    return val.customProperty;
  }
}
```

---

## 5.2 Custom Type Predicates (`val is Type`) & Assertion Functions

Khi logic kiểm tra phức tạp và cần tách thành hàm riêng, hàm thông thường trả về `boolean` sẽ **không giúp** TypeScript thu hẹp kiểu. Bạn phải dùng cú pháp `value is T`.

```typescript
interface AdminUser {
  role: "admin";
  permissions: string[];
}

function isAdmin(user: any): user is AdminUser {
  return (
    typeof user === "object" &&
    user !== null &&
    user.role === "admin" &&
    Array.isArray(user.permissions)
  );
}

function assertIsAdmin(user: any): asserts user is AdminUser {
  if (!isAdmin(user)) {
    throw new Error("Truy cập bị từ chối: Yêu cầu quyền Admin!");
  }
}

function handleDashboard(account: unknown) {
  assertIsAdmin(account);
  console.log(account.permissions.length);
}
```

---

## 5.3 Discriminated Unions & Exhaustive Checking với `never`

Discriminated Union (Tagged Union) là mẫu thiết kế mạnh mẽ nhất của TypeScript để quản lý trạng thái máy (State Machine), kết quả API, hoặc xử lý sự kiện.

### Bí kíp Kiểm tra vét cạn (Exhaustive Checking)
Sử dụng kiểu `never` để TypeScript cảnh báo ngay lúc compile nếu chúng ta quên xử lý một nhánh state:

```typescript
type NetworkState =
  | { status: "idle" }
  | { status: "loading" }
  | { status: "success"; data: string[] }
  | { status: "error"; error: Error };

function renderState(state: NetworkState) {
  switch (state.status) {
    case "idle":
      return "Sẵn sàng";
    case "loading":
      return "Đang tải dữ liệu...";
    case "success":
      return `Thành công: ${state.data.length} bản ghi`;
    case "error":
      return `Lỗi: ${state.error.message}`;
    default: {
      const _unreachable: never = state;
      throw new Error(`Chưa xử lý trạng thái: ${_unreachable}`);
    }
  }
}
```

---

# Phần 6: Generic Programming & Hệ Thống Kiểu Nâng Cao

## 6.1 Generics căn bản & Constraints (`extends`)

Generic cho phép viết mã linh hoạt, tái sử dụng cao nhưng vẫn giữ nguyên vẹn thông tin kiểu của dữ liệu truyền vào.

```typescript
function logLength<T extends { length: number }>(item: T): T {
  console.log(`Độ dài: ${item.length}`);
  return item;
}

logLength("Hello World");
logLength([1, 2, 3]);
```

---

## 6.2 Keyof, Indexed Access (`T[K]`) & Lookup Types

```typescript
interface DatabaseRecord {
  id: string;
  payload: {
    ip: string;
    userAgent: string;
  };
}

type RecordKey = keyof DatabaseRecord;
type PayloadType = DatabaseRecord["payload"];

function getProp<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}
```

---

## 6.3 Mapped Types & Key Remapping (`as`)

Tạo ra một cấu trúc kiểu mới dựa trên việc lặp qua các key của kiểu cũ, kèm khả năng thêm/bớt cờ `readonly`, `?`, hoặc biến đổi tên key bằng từ khóa `as`.

```typescript
interface Product {
  id: string;
  name: string;
  price: number;
}

type PropertyGetters<T> = {
  [K in keyof T as `get${Capitalize<string & K>}`]: () => T[K];
};

type ProductGetters = PropertyGetters<Product>;
```

---

## 6.4 Conditional Types & Từ khóa `infer`

Conditional Type có dạng `T extends U ? X : Y` (Tương tự toán tử ba ngôi của kiểu dữ liệu).

Từ khóa `infer` cho phép **trích xuất một kiểu con bên trong một kiểu phức tạp** (như kiểu phần tử mảng, kiểu trả về của Promise, kiểu tham số hàm).

```typescript
type UnwrapArray<T> = T extends (infer Element)[] ? Element : T;

type A = UnwrapArray<string[]>;
type B = UnwrapArray<number>;

type UnwrapPromise<T> = T extends Promise<infer Result> ? Result : T;
type UserPromise = UnwrapPromise<Promise<{ id: number }>>;
```

---

## 6.5 Template Literal Types thực chiến

Ghép nối chuỗi kiểu tĩnh, kết hợp với union để tạo ra hệ thống routing hoặc event system cực kỳ chặt chẽ:

```typescript
type HttpMethod = "GET" | "POST" | "DELETE";
type ApiRoute = "/users" | "/products";

type EndpointSignature = `${HttpMethod} ${ApiRoute}`;

type EventGroup = "user" | "order";
type EventAction = "created" | "deleted" | "updated";
type SystemEvent = `${EventGroup}:${EventAction}`;
```

---

## 6.6 Bảng tra cứu Utility Types có sẵn & Cách tự viết lại

Hiểu được cách hoạt động bên dưới của các Utility Type giúp nâng cao năng lực viết TypeScript vượt bậc:

| Utility Type | Mô tả công dụng | Cách TypeScript tự viết bên dưới |
| :--- | :--- | :--- |
| `Partial<T>` | Biến mọi thuộc tính thành optional (`?`) | `type Partial<T> = { [P in keyof T]?: T[P]; }` |
| `Required<T>`| Loại bỏ toàn bộ `?`, bắt buộc mọi trường | `type Required<T> = { [P in keyof T]-?: T[P]; }` |
| `Readonly<T>`| Đóng băng mọi trường, không cho sửa | `type Readonly<T> = { readonly [P in keyof T]: T[P]; }` |
| `Pick<T, K>` | Chọn lọc một số key nhất định từ `T` | `type Pick<T, K extends keyof T> = { [P in K]: T[P]; }` |
| `Omit<T, K>` | Loại bỏ các key `K` khỏi `T` | `type Omit<T, K extends keyof any> = Pick<T, Exclude<keyof T, K>>` |
| `Exclude<T, U>`| Lọc bỏ các kiểu thuộc `U` khỏi union `T` | `type Exclude<T, U> = T extends U ? never : T` |
| `Extract<T, U>`| Lấy phần giao giữa hai union `T` và `U` | `type Extract<T, U> = T extends U ? T : never` |
| `NonNullable<T>`| Loại bỏ `null` và `undefined` khỏi kiểu | `type NonNullable<T> = T & {}` |
| `ReturnType<T>`| Lấy kiểu kết quả trả về của một hàm | `type ReturnType<T extends (...args: any) => any> = T extends (...args: any) => infer R ? R : any` |

---

# Phần 7: Bất đồng bộ (Asynchronous) & Luồng Sự Kiện (Event Loop)

## 7.1 Bản chất Event Loop: Call Stack, Web APIs, Microtask vs Macrotask

JavaScript là ngôn ngữ đơn luồng (Single-threaded). Nó xử lý đa nhiệm thông qua cơ chế **Event Loop**:

```
┌──────────────────────────────────────────────┐
│                  Call Stack                  │
└──────────────────────────────────────────────┘
                       ▲
                       │ Khi Call Stack rỗng
      ┌────────────────┴────────────────┐
      │      1. Microtask Queue         │
      │  (Promise.then, queueMicrotask) │
      └─────────────────────────────────┘
                       ▲
                       │ Sau khi Microtask Queue cạn
      ┌────────────────┴────────────────┐
      │       2. Macrotask Queue        │
      │ (setTimeout, setInterval, I/O)  │
      └─────────────────────────────────┘
```

### Câu hỏi phỏng vấn kinh điển về Thứ tự In:
```javascript
console.log("1");

setTimeout(() => {
  console.log("2");
}, 0);

Promise.resolve().then(() => {
  console.log("3");
});

console.log("4");
```

---

## 7.2 Vòng đời Promise & Async/Await

Một `Promise` có 3 trạng thái: `pending` (chờ), `fulfilled` (thành công), `rejected` (thất bại).

- `async/await` là cú pháp giúp viết mã bất đồng bộ trông giống như mã đồng bộ tuần tự.
- Bên dưới, hàm `async` luôn luôn đóng gói kết quả trả về trong một `Promise`.

```typescript
async function fetchAccountData(id: string): Promise<User> {
  try {
    const res = await fetch(`/api/users/${id}`);
    if (!res.ok) {
      throw new Error(`HTTP Error: ${res.status}`);
    }
    return (await res.json()) as User;
  } catch (err: unknown) {
    const message = err instanceof Error ? err.message : "Lỗi không xác định";
    throw new Error(`Không thể lấy dữ liệu user: ${message}`);
  }
}
```

---

## 7.3 Promise Concurrency: All, AllSettled, Race, Any

| Phương thức | Hành vi khi thành công | Hành vi khi có 1 promise thất bại |
| :--- | :--- | :--- |
| `Promise.all` | Trả về mảng kết quả khi **tất cả** thành công | **Dừng ngay lập tức** khi có bất kỳ task nào reject (Fail-fast) |
| `Promise.allSettled` | Chờ **tất cả hoàn tất** (cả resolve lẫn reject), trả về status từng task | Không bao giờ reject; luôn trả về trạng thái chi tiết của từng promise |
| `Promise.race` | Lấy kết quả của promise hoàn thành **đầu tiên** (dù resolve hay reject) | Reject ngay nếu promise về nhất bị reject |
| `Promise.any` | Trả về promise **thành công đầu tiên** | Chỉ reject (ném `AggregateError`) khi **toàn bộ** đều thất bại |

```typescript
function withTimeout<T>(promise: Promise<T>, ms: number): Promise<T> {
  const timeout = new Promise<never>((_, reject) =>
    setTimeout(() => reject(new Error("Timeout sau " + ms + "ms")), ms)
  );
  return Promise.race([promise, timeout]);
}
```

---

## 7.4 Iterators, Generators & Async Iterables

- **Generator (`function*`)**: Hàm có khả năng tạm dừng thực thi (`yield`) và tiếp tục (`next()`), duy trì trạng thái nội bộ. Rất tối ưu khi tạo ra các luồng dữ liệu vô hạn hoặc lazy processing mà không tốn RAM.
- **Async Generator (`async function*`)**: Kết hợp generator với bất đồng bộ, tiêu chuẩn vàng để stream dữ liệu từng dòng (chunk) từ file lớn hoặc SSE / WebSocket.

```typescript
async function* streamLines(url: string): AsyncGenerator<string> {
  const response = await fetch(url);
  const reader = response.body?.getReader();
  if (!reader) return;

  const decoder = new TextDecoder();
  while (true) {
    const { done, value } = await reader.read();
    if (done) break;
    yield decoder.decode(value);
  }
}

async function consume() {
  for await (const chunk of streamLines("https://api.example.com/stream")) {
    console.log("Nhận được gói dữ liệu:", chunk);
  }
}
```

---

# Phần 8: Cấu hình Dự án & Thiết lập Tooling Chuẩn Enterprise

## 8.1 Giải mã các cờ cốt lõi trong `tsconfig.json`

Một file cấu hình chuẩn mực, bảo vệ tối đa mã nguồn:

```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    
    "strict": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "noUncheckedIndexedAccess": true,
    "exactOptionalPropertyTypes": true,
    
    "rootDir": "./src",
    "outDir": "./dist",
    "declaration": true,
    "sourceMap": true,
    
    "esModuleInterop": true,
    "skipLibCheck": true
  },
  "include": ["src/**/*"]
}
```

---

## 8.2 Module Resolution: CommonJS vs ESM (NodeNext)

Trong môi trường ESM hiện đại (`"module": "NodeNext"`):
- Bạn **bắt buộc phải ghi rõ đuôi file `.js`** khi import module tương đối, ngay cả khi đang viết mã nguồn trong file `.ts`!
- Không còn các biến toàn cục cũ của CommonJS như `__dirname` và `__filename`. Thay vào đó, dùng `import.meta.url`.

```typescript
import { helper } from "./utils.js";

import { fileURLToPath } from "node:url";
import { dirname } from "node:path";

const __filename = fileURLToPath(import.meta.url);
const __dirname = dirname(__filename);
```

---

## 8.3 Ambient Declarations (`.d.ts`) & Module Augmentation

Khi làm việc với các thư viện bên thứ 3 không có sẵn types, hoặc muốn thêm các thuộc tính mở rộng cho các global module:

```typescript
declare namespace Express {
  export interface Request {
    currentUser?: {
      userId: string;
      role: "admin" | "user";
    };
  }
}

declare module "*.png" {
  const content: string;
  export default content;
}
```

---

# Phần 9: Tổng hợp Lỗi Thường Gặp & Best Practices Checklist

## Bảng Tra Cứu Sự Cố & Giải Pháp Thực Tế

| Vấn đề / Lỗi | Nguyên nhân gốc rễ | Giải pháp chuẩn |
| :--- | :--- | :--- |
| `Cannot read properties of undefined (reading 'xyz')` | Cố đọc thuộc tính từ một giá trị `null` hoặc `undefined` | Sử dụng Optional Chaining `obj?.xyz` hoặc kết hợp với default value `??`. Bật `"strictNullChecks"`. |
| Mảng truy cập ngoài index không báo lỗi | TypeScript mặc định coi `arr[999]` luôn trả về kiểu `T` (mặc dù thực tế là `undefined`) | Kích hoạt cờ `"noUncheckedIndexedAccess": true` trong `tsconfig.json`. |
| Ép kiểu `as TargetType` gây lỗi runtime | Dùng `as` chỉ đánh lừa compiler, không hề convert dữ liệu thật lúc chạy | Viết Custom Type Guard (`val is T`) hoặc dùng thư viện runtime schema như Zod/Valibot để validate trước khi cast. |
| Mất ngữ cảnh `this` khi truyền callback | Hàm được gọi tách rời khỏi object sở hữu nó | Dùng Arrow Function hoặc gọi `.bind(this)` tại constructor. |
| `Object.keys()` trả về `string[]` thay vì union key | Vì tính chất *Structural Subtyping* của TS, một object runtime có thể chứa nhiều key hơn interface định nghĩa | Ép kiểu có chủ đích `(Object.keys(obj) as (keyof typeof obj)[])` nếu dám chắc object không bị thừa trường. |
| Không bắt được lỗi trong async function | Quên từ khóa `await` bên trong khối lệnh `try...catch` | Luôn kiểm tra kỹ mọi promise đều có `await` hoặc gắn `.catch()`. |

---

## Checklist Viết Code TypeScript Chuyên Nghiệp

- [ ] **Tuyệt đối không dùng `any` bừa bãi**: Thay thế bằng `unknown` nếu chưa biết cấu trúc, hoặc dùng Generics.
- [ ] **Bật toàn bộ cờ Strict**: Đảm bảo `strict: true` và `noUncheckedIndexedAccess: true`.
- [ ] **Ưu tiên Immutability**: Dùng `readonly`, `ReadonlyArray<T>`, và `as const` cho các mảng/object hằng số.
- [ ] **Tận dụng Discriminated Unions**: Luôn có một trường phân biệt (`type` hoặc `status`) và dùng Exhaustive Checking với `never`.
- [ ] **Phân biệt rõ ràng Compile-time vs Runtime**: Kiểm tra dữ liệu ngoại lai từ Network/File bằng Type Guard hoặc Schema Validator trước khi xử lý.
