# 条件分岐

## 条件分岐のネスト化による可読性の低下

**if文で多重にネストした場合**
### 例
```
//生存しているかを判定
if(0 < member.hitPoint) {
  // 行動可能か判定
  if(member.canAct()) {
    // 魔法が残存しているかを判定
    if(magic.costMagicPoint <= member.magicPoint>) {
      member.consumeMagicPoint(magic.costMagicPoint)
      member.chant(magic)
    }
  }
}
```
- 生存していること
- 行動可能であること
- 魔法力が残存していること

このようなif文が入れ子構造となっていることを**ネスト**という<br>

### ネストしていると何が不味いのか
- コードの見通しが悪くなっていく
- どこからどこまでがif文の構造の中なのか、読み難しくなっていく
- 仕様変更が大変
よってメンバー全体が疲弊していく。<br>

## 早期returnでネスト解消
この問題を解決するためには、早期returnという方法を使います。<br>
**早期returnとは、条件を満たしていない場合に直ちに、returnで抜けてしまう、という手法です。**
### 例
```
if(member.hitPoint <= 0>) return 
if(!member.canAct()) return
if(member.magicPoint < magic.costMagicPoint) return
member.consumeMagicPoint(magic.costMagicPoint)
member.chant(magic)
```
**早期returnの形にする場合は、元の式を反転させます。**
生存している場合→生存していない場合<br>
これでネストを解消することができました。<br>
**早期returnのもう一つの利点**
条件ロジックと実行ロジックを分離できる点です。<br>
- ロジックの追加が容易になる
- 条件と実行ロジックを読み解くことが容易になる

### 早期returnでelse句も解消できる

