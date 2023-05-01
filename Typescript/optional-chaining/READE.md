# オプショナルチェイニング

> アクセスされるオブジェクトが null や undefined でも使用することができる

## 記法

```
user?.age
```

## プロパティ呼び出しのオプショナルチェイニング
### 例

```
type Human = {
   name : string
   age  : number
}
```

**age は number | undefined 型**  

```
function useMaybeHuman(human:Human | undefined) { 
   const age = human?.age
   console.log(age)
}
```

## 関数呼び出しのオプショナルチェイニング  
### 例

```
type GetTimeFunc = () => Date
```

**timeOrUndefined は Date | undefined 型**  

```
function useTime(getTimeFunc:GetTimeFunc | undefined) {
   const timeOrUndefined = getTimeFunc?.()
}
```

## メソッド呼び出しのオプショナルチェイニング
### 例

```
type User = {
   isAdmin() : boolean
}
``` 

**userがnullならば、結果がundefinedになる**  

```
function checkForAdultUser(user:User | mill) {
   if(user?.isAdmin()) {
      showSpecialContents(user)  
   }
}
``` 

# オプショナルチェイニングの応用

Dateオブジェクトは`toString()`メソッドを持ち、自身を文字列に変換した結果を返すものです。
これは、`getTimeFunc?.()`の結果に対して、さらにその`toString()`にアクセスしているように
見えます。

```
type GetTimeFunc = () => Date;

function useTime(getTimeFunc: GetTimeFunc | undefined) {
   const timeStringOrUndefined = getTimeFunc?.().toString()
}
```

これは特にコンパイルエラーは起きません。
ですが、`getTimeFunc?.()`が`undefined`だった場合 `undefined`に`toString()`メソッドが呼び出される可能性が
あるように見えてしまいます。
当然そのような場合はコンパイルエラーになるはずです。でも上の例ではなりません。

### ここにオプショナルチェイニングのもう1つの特徴があります

**?.はそれ以降のプロパティアクセス・関数呼び出し・メソッド呼び出しをまとめて飛ばし効果を持つ**

`getTimeFunc`が`undefined`だった場合、
`?.().toString()`以降はまとめて飛ばされ、結果`undefined`が返ります

まとめて飛ばされる部分を **オプショナルチェイン** と呼びます。