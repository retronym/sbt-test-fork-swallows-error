## sbt-test-fork-swallows-error

Test project to demonstrate a bug in error handling
in SBT.

Minimized from the scala/scala SBT build, which I found does not
fail if we introduce a binary incompatibility between the new
library and the reference version of partest.

```
⚡ sbt
[info] Loading global plugins from /Users/jz/.sbt/0.13/plugins
[info] Loading project definition from /Users/jz/code/scratch/project
[info] Set current project to scratch (in build file:/Users/jz/code/scratch/)
[master] scratch: test
[error] Uncaught exception when running tests: java.lang.Throwable
[trace] Stack trace suppressed: run last test:test for the full output.
Exception in thread "Thread-4" java.io.EOFException
    at java.io.ObjectInputStream$BlockDataInputStream.peekByte(ObjectInputStream.java:2626)
    at java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1321)
    at java.io.ObjectInputStream.readObject(ObjectInputStream.java:373)
    at sbt.React.react(ForkTests.scala:114)
    at sbt.ForkTests$$anonfun$mainTestTask$1$Acceptor$2$.run(ForkTests.scala:74)
    at java.lang.Thread.run(Thread.java:745)
[success] Total time: 0 s, completed 31/08/2016 2:30:46 PM
[master] scratch: last
[debug] [naha]
[debug] [naha] Initial source changes:
[debug] [naha]  removed:Set()
[debug] [naha]  added: Set()
[debug] [naha]  modified: Set()
[debug] [naha] Invalidated products: Set()
[debug] [naha] External API changes: API Changes: Set()
[debug] [naha] Modified binary dependencies: Set()
[debug] [naha] Initial directly invalidated sources: Set()
[debug] [naha]
[debug] [naha] Sources indirectly invalidated by:
[debug] [naha]  product: Set()
[debug] [naha]  binary dep: Set()
[debug] [naha]  external source: Set()
[debug] All initially invalidated sources: Set()
[debug] Copy resource mappings:
[debug]
[debug] [naha]
[debug] [naha] Initial source changes:
[debug] [naha]  removed:Set()
[debug] [naha]  added: Set()
[debug] [naha]  modified: Set()
[debug] [naha] Invalidated products: Set()
[debug] [naha] External API changes: API Changes: Set()
[debug] [naha] Modified binary dependencies: Set()
[debug] [naha] Initial directly invalidated sources: Set()
[debug] [naha]
[debug] [naha] Sources indirectly invalidated by:
[debug] [naha]  product: Set()
[debug] [naha]  binary dep: Set()
[debug] [naha]  external source: Set()
[debug] All initially invalidated sources: Set()
[debug] Copy resource mappings:
[debug]
[debug] Subclass fingerprints: List()
[debug] Annotation fingerprints: List((my,true,build.MyFramework$$anon$1@75c5bd2a))
[debug] javaOptions: List()
[debug] Forking tests - parallelism = false
[debug] Create a single-thread test executor
[error] Uncaught exception when running tests: java.lang.Throwable
sbt.ForkMain$ForkError: java.lang.Throwable: null
    at build.MyRunner.tasks(MyFramework.scala:14)
    at sbt.ForkMain$Run.runTests(ForkMain.java:253)
    at sbt.ForkMain$Run.run(ForkMain.java:139)
    at sbt.ForkMain.main(ForkMain.java:121)
[debug] Summary for my not available.
[success] Total time: 0 s, completed 31/08/2016 2:30:46 PM
[debug] > shell
[debug] Running task... Cancel: Null, check cycles: false, forcegc: true
```