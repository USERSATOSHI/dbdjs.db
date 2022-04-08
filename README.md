[![dbd.js](https://cdn.discordapp.com/attachments/817018613046312990/846181270840279050/dbdjs.png)](https://discord.com/invite/HMUfMXDQsV)

# dbdjs.db

[![Discord Server](https://img.shields.io/discord/773352845738115102?color=5865F2&logo=discord&logoColor=white)](https://discord.com/invite/HMUfMXDQsV)
[![NPM Downloads](https://img.shields.io/npm/dt/dbdjs.db.svg?maxAge=3600)](https://www.npmjs.com/package/dbdjs.db)
[![NPM Version](https://img.shields.io/npm/v/dbdjs.db.svg?maxAge=3600)](https://www.npmjs.com/package/dbdjs.db)

## Table Of Contents

- [About](#about)

- [Examples](#examples)
  - [KeyValue](#keyvalue)
    - [Setup](#setup)
    -[BulkSet](#bulkset)
    - [Set](#set)
    - [Get](#get)
    - [Get All](#get-all)
    - [Delete](#delete)
    - [Ping](#ping)
    - [TablePing](#tableping)
- [Links](#links)

## About

dbdjs.db is a DBMS made in TS to support many database types like KeyValue , WideColumnar , Relational etc
## Examples
### KeyValue
#### Setup

<details> 
<summary>CJS</summary>

```js
const { KeyValue } = require("dbdjs.db");

const db = new KeyValue({
  path: "./database/",
  tables: ["test"],
});

db.once("ready", () => {
  console.log("Database ready!");
});

db.connect();
```

</details>
<details>
<summary>ESM</summary>

```js
import { KeyValue } from "dbdjs.db";

const db = new KeyValue({
  path: "./database/",
  tables: ["test"],
});

db.once("ready", () => {
  console.log("Database ready!");
});

db.connect();
```

</details>

#### BulkSet


```js
await db.bulkSet("test",{
  key : "Number", {
  value: 1,
}
},{
  key : "String", {
  value: "hello World",
}
});
```

#### Set

```js
await db.set("test", "Number", {
  value: 1,
});

await db.set("test", "String", {
  value: "hello World",
});

await db.set("test", "BigInt", {
  value: 2n,
});  // { value : 1 , type : "bigint" } || {value : BigInt("1223432") }

await db.set("test", "Boolean", {
  value: true,
});

await db.set("test", "Object", {
  value: { hello: "world" },
});

await db.set("test", "Arrays", {
  value: [1, 2, 3, 4, 5],
});

await db.set("test", "Date", {
  value: new Date(), 
}); // { value : 1234565432 , type : "date" } || {value : "12/12/2022", type : "date" }

await db.set("test", "null", {
  value: null,
});
```

#### Get

```js
const string = await db.get("test", "String");
const numbers = await db.get("test", "Numbers");
```

####  All

```js
const lerefAndApple = await db.all("test", undefined, Infinity); // Setting limit as Infinity will return all data
```

#### Delete

```js
await db.delete("test", "fruits");
await db.delete("test", "leref");
```

#### Clear

```js
db.clear("test");
```

#### Ping

```js
db.ping;
```

#### TablePing

```js
db.tablePing("test"); 
```

## Links

dbdjs.db was created for ~~[dbd.js](https://www.npmjs.com/package/dbd.js)~~ [aoi.js](https://www.npmjs.com/aoi.js) but now, it's available for anyone to learn and use.

- [Website](https://aoi.js.org)
- [Docs](https://usersatoshi.github.io/dbdjs.db/)
- [Discord Server](https://discord.com/invite/HMUfMXDQsV)
