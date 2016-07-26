# Serializable

```
type mismatch;
 found   : Serializable
 required: Option[String]
```

Serializableってなんだ？と思い色々調べてみたが結局たいしたことありませんでした

単純に返り値としてOptionを返したいときはmatchでそれぞれ`None`か`Some`で包んであげなくてはならないっていう話


- サンプル

```
import scala.util.Random
val r = new Random
val a = r.nextInt(10)

val b = a % 2 match {
  case 0 => "even"
  case 1 => None
}

// java.io.Serializable = None
```

- 正しい例

```
import scala.util.Random
val r = new Random
val a = r.nextInt(10)

a % 2 match {
  case 0 => Some("even")
  case 1 => None
}

// Option[String] = None
```


はい、30分無駄にしました


