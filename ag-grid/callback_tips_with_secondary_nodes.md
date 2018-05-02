# [ag-grid] cellRendererとかvalueGetterとかセルに対してコールバック関数を渡すときのtips

pivotやgroupingなどを使ってコールバックを設定するとコールバックの引数が変わってくる

単純のparams.valueだけしか使ってなければ問題ないがparams.dataとか他のカラムのデータを使って何かしてたりすると問題が起きる(参照できないエラー)

なので再集計がされたnodeがわたってきてるのかそうでないのかで分岐が必要になってくる

- 集計データ

params.node.aggData

- ただの行データ

params.data or params.node.data

params.dataだと集計行の時にデータが入ってこない入ってこない

なので両方共通で扱いたい場合は

```
function gridCallback(params) {
  const data = params.node.data || params.node.aggData;
}
```

などとする必要がある


