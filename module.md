# JavaScriptのモジュールは２つ

## ComonnJS形式 / ES Module形式

それぞれ書き方が全く違う

<br>

scriptタグを書く際に **type="module"** と記述するとモジュールとして扱える。

```js
<script type="module" src="○○.js"></script>
```

## - export / import の種類 -

<br>

<details>
<summary>named export / import</summary>

## named export / import

<br>

- 変数 : 個々の機能を export

```js
---- user.js ----

const name = "山本";

export { name };
```

```js
---- index.js ----

import { name } from "./user.js";
```

<br>

- 変数 : 複数まとめて export

```js
---- user.js ----

const name = "山本";
const name2 = "太田";

export { name, name2 };
```

```js
---- index.js ----

import { name, name2 } from "./user.js";
```

<br>

- 変数 : 宣言と同時に export
  
```js
---- user.js ----

export const name = "山本";

export const name2 = "太田";
export { name, name2 };
```

```js
---- index.js ----

import { name, name2 } from "./user.js";
```

<br>

- 関数 : 複数まとめて export

```js
---- user.js ----

function log(value) {
    console.log(value);
}
const name = "山本";

export { name, log };
```

```js
---- index.js ----

import { name, log } from "./user.js";
```

<br>

- 関数 : 宣言と同時に export
  
```js
---- user.js ----

export function log(value) {
    console.log(value);
}
```

```js
---- index.js ----

import { log } from "./user.js";
```

<br>

## - エイリアス -
エイリアスとは、別名という意味。
<br>
識別子に **as** とつけてその後に別名を付けることができる。
<br>
一般的には import でのエイリアスが多い。

<br>

- named export でのエイリアス

```js
---- user.js ----

const name = "山本";

export { name as yama };
```

```js
---- index.js ----

import  { yama } from "./user.js";
```

<br>

- named import でのエイリアス

```js
---- user.js ----

const name = "山本";

export { name };
```

```js
---- index.js ----

import  { name as yama } from "./user.js";
```

</details>

<details>
<summary>default export / import</summary>

## default export / import
<br>
export default では1モジュールに対して1回しか使えない。
<br>
import では { } で囲わずに記述する。

<br>
<br>

- 変数 : export default

```js
---- user.js ----

const name = "山本";

export default name;
```

```js
---- index.js ----

import name from "./user.js";
```

<br>

- 関数 : 宣言と同時に export
<br>
宣言と同時に exportできるのは関数のみ。定数を宣言と同時に export するとエラーになる。
<br>
```js
---- user.js ----

const log = function() {
    console.log()
}

export default log;
```

```js
---- index.js ----

import log from "./user.js";
```
</details>
