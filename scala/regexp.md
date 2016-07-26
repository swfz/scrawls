# scalaで後方参照

matchでマッチした箇所をそのまま使うことが出来る

```
val id = "323-232-aaa"

val p = """(\d+-\d+)-(.+)""".r

id match {
  case p(prefix,suffix) => println(prefix,suffix)
  case _ => println("not match")
}
```


