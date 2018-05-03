# youtubeの動画情報を取得する

youtubeの動画情報、例えばwidth,heightなどの情報はAPIkから取れるようになっているがメタ情報(サイズとか)に関しては動画をアップロードしたアカウントでのAPIアクセスじゃないと取れないらしい

どうしても縦横サイズが欲しかったのでダウンロードして見るかーと思って調べてみたらこれ一つでやりたいことは全部完結できた

https://github.com/rg3/youtube-dl

READMEどうりに

- install

```
sudo curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl
sudo chmod a+rx /usr/local/bin/youtube-dl
```

- 動画情報を取得する

```
$ youtube-dl 'https://www.youtube.com/watch?v=ID......' --write-info-json
$ ls
{videoname}.mp4-{id}.info.json
{videoname}.mp4-{id}.mp4
$ cat {videoname}.mp4-{id}.info.json | jq '.width,.height'
406
720
```

これだけでファイル名.info.jsonが生成されてその中にwidth,heightなどの情報も入っている

すごい

