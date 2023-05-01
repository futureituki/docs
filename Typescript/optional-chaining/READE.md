# オプショナルチェイニング

> アクセスされるオブジェクトが null や undefined でも使用することができる

## 記法
`user?.age`

## プロパティ呼び出しのオプショナルチェイニング
### 例
`type Human = {`
   `name : string`
   `age  : number`
`}`

`function useMaybeHuman(human:Human | undefined)`
   **age は number | undefined 型**
   `const age = human?.age`
   `console.log(age)`
`}`

## 関数呼び出しのオプショナルチェイニング
### 例
`type GetTimeFunc = () => Date`

`function useTime(getTimeFunc:GetTimeFunc | undefined)`
   **timeOrUndefined は Date | undefined 型**
   `const timeOrUndefined = getTimeFunc?.()`
`}`

## メソッド呼び出しのオプショナルチェイニング
### 例
`type User = {`
   `isAdmin() : boolean`
`}`
**userがnullならば、結果がundefinedになる**
`function checkForAdultUser(user:User | mill)`
   `if(user?.isAdmin()) {`
      `showSpecialContents(user)`      
   `}`
`}`