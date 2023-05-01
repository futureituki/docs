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

**age は number | undefined 型**  

`function useMaybeHuman(human:Human | undefined) {`  
   `const age = human?.age`  
   `console.log(age)`  
`}`  

## 関数呼び出しのオプショナルチェイニング  
### 例

`type GetTimeFunc = () => Date`  

**timeOrUndefined は Date | undefined 型**  

`function useTime(getTimeFunc:GetTimeFunc | undefined) {`  
   `const timeOrUndefined = getTimeFunc?.()`  
`}`  

## メソッド呼び出しのオプショナルチェイニング
### 例

`type User = {`  
   `isAdmin() : boolean`  
`}`  

**userがnullならば、結果がundefinedになる**  

`function checkForAdultUser(user:User | mill) {`  
   `if(user?.isAdmin()) {`  
      `showSpecialContents(user)`      
   `}`  
`}`  