# リテラル型

### ４種類のリテラル型
**プリミティブ型をさらに細分化した型**

#### 例
**これは"foo"という文字列のみが属するリテラル型**
```
type FooString = 'foo'
```
**OK**
```
const foo:FooString = 'foo'
```
**エラー : Type 'bar' is not assignable to type "foo"**
```
const bar:FooString = 'bar'
```

