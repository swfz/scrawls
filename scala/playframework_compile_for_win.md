# Windowsでplayframeworkコンパイル時のstackoverflowエラーに間して

コンパイル途中でstackoverflowで落ちるというはじめる以前の問題に直面

```
> run
[info] Compiling 97 Scala sources to C:\Users\....\....\p2\lib\target\scala-2.11\classes...
[trace] Stack trace suppressed: run last lib/compile:compileIncremental for the full output.
[error] (lib/compile:compileIncremental) java.lang.StackOverflowError
[error] Total time: 133 s, completed 2016/07/20 17:08:44
```

どこかの記事か忘れてしまったがXmsとXmx合わせて1500M以上に設定してしまうと出るらしい

なので抑えて再実行する

- 環境変数を設定

```
$ set SBT_OPTS= -Xms400M -Xmx800M -Xss1M -XX:MaxMetaspaceSize=1800M
```

.....
.....
.....

- 再実行

```
> run
[info] Compiling 97 Scala sources to C:\Users\....\....\p2\lib\target\scala-2.11\classes...

--- (Running the application, auto-reloading is enabled) ---

[info] p.a.l.c.ActorSystemProvider - Starting application default Akka system: application
[info] p.c.s.NettyServer - Listening for HTTP on /0:0:0:0:0:0:0:0:9000

(Server started, use Ctrl+D to stop and go back to the console...)
```

出来た！

