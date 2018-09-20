## Scripts

### jps -l

Above shell command prints the currently running process ids (pids) of java.

### jstack -l <pid>

Above shell command prints the whole thread dump for the process having process id as "pid"

## How to analyse the thread dump :
 Below is a sample thread dump from a running java process.

```
Full thread dump OpenJDK 64-Bit Server VM (25.152-b8 mixed mode):

"ApplicationImpl pooled thread 50" #138 prio=4 os_prio=0 tid=0x00007fc15033a800 nid=0x3690 waiting on condition [0x00007fc1414f7000]
   java.lang.Thread.State: TIMED_WAITING (parking)
	at sun.misc.Unsafe.park(Native Method)
	- parking to wait for  <0x00000000e1c72618> (a java.util.concurrent.SynchronousQueue$TransferStack)
	at java.util.concurrent.locks.LockSupport.parkNanos(LockSupport.java:215)
	at java.util.concurrent.SynchronousQueue$TransferStack.awaitFulfill(SynchronousQueue.java:460)
	at java.util.concurrent.SynchronousQueue$TransferStack.transfer(SynchronousQueue.java:362)
	at java.util.concurrent.SynchronousQueue.poll(SynchronousQueue.java:941)
	at java.util.concurrent.ThreadPoolExecutor.getTask(ThreadPoolExecutor.java:1066)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1127)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"ApplicationImpl pooled thread 48" #136 daemon prio=4 os_prio=0 tid=0x00007fc190835000 nid=0x3346 waiting on condition [0x00007fc14bdfe000]
   java.lang.Thread.State: TIMED_WAITING (parking)
	at sun.misc.Unsafe.park(Native Method)
	- parking to wait for  <0x00000000e1c72618> (a java.util.concurrent.SynchronousQueue$TransferStack)
	at java.util.concurrent.locks.LockSupport.parkNanos(LockSupport.java:215)
	at java.util.concurrent.SynchronousQueue$TransferStack.awaitFulfill(SynchronousQueue.java:460)
	at java.util.concurrent.SynchronousQueue$TransferStack.transfer(SynchronousQueue.java:362)
	at java.util.concurrent.SynchronousQueue.poll(SynchronousQueue.java:941)
	at java.util.concurrent.ThreadPoolExecutor.getTask(ThreadPoolExecutor.java:1066)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1127)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"Attach Listener" #101 daemon prio=9 os_prio=0 tid=0x00007fc1a80e2000 nid=0x276b waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

   Locked ownable synchronizers:
	- None

"Process Proxy: MainApplication" #84 prio=6 os_prio=0 tid=0x00007fc1507a3000 nid=0x26cb runnable [0x00007fc160481000]
   java.lang.Thread.State: RUNNABLE
	at sun.nio.ch.EPoll.epollWait(Native Method)
	at sun.nio.ch.EPollPort$EventHandlerTask.poll(EPollPort.java:194)
	at sun.nio.ch.EPollPort$EventHandlerTask.run(EPollPort.java:268)
	at sun.nio.ch.AsynchronousChannelGroupImpl$1.run(AsynchronousChannelGroupImpl.java:112)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e293bfe8> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"RMI TCP Connection(341)-127.0.0.1" #73 daemon prio=4 os_prio=0 tid=0x00007fc15c034000 nid=0x268c runnable [0x00007fc13d00c000]
   java.lang.Thread.State: RUNNABLE
	at java.net.SocketInputStream.socketRead0(Native Method)
	at java.net.SocketInputStream.socketRead(SocketInputStream.java:116)
	at java.net.SocketInputStream.read(SocketInputStream.java:171)
	at java.net.SocketInputStream.read(SocketInputStream.java:141)
	at java.io.BufferedInputStream.fill(BufferedInputStream.java:246)
	at java.io.BufferedInputStream.read(BufferedInputStream.java:265)
	- locked <0x00000000d2acf518> (a java.io.BufferedInputStream)
	at java.io.FilterInputStream.read(FilterInputStream.java:83)
	at sun.rmi.transport.tcp.TCPTransport.handleMessages(TCPTransport.java:550)
	at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.run0(TCPTransport.java:826)
	at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.lambda$run$0(TCPTransport.java:683)
	at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler$$Lambda$1509/967944393.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.run(TCPTransport.java:682)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e38f1540> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"RMI RenewClean-[127.0.0.1:44621]" #72 daemon prio=4 os_prio=0 tid=0x00007fc1a8140800 nid=0x2689 in Object.wait() [0x00007fc13d10e000]
   java.lang.Thread.State: TIMED_WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:143)
	- locked <0x00000000e3ab8690> (a java.lang.ref.ReferenceQueue$Lock)
	at sun.rmi.transport.DGCClient$EndpointEntry$RenewCleanThread.run(DGCClient.java:553)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"RMI Scheduler(0)" #71 daemon prio=4 os_prio=0 tid=0x00007fc1a8140000 nid=0x2688 waiting on condition [0x00007fc13d20f000]
   java.lang.Thread.State: TIMED_WAITING (parking)
	at sun.misc.Unsafe.park(Native Method)
	- parking to wait for  <0x00000000e3b0f9e8> (a java.util.concurrent.locks.AbstractQueuedSynchronizer$ConditionObject)
	at java.util.concurrent.locks.LockSupport.parkNanos(LockSupport.java:215)
	at java.util.concurrent.locks.AbstractQueuedSynchronizer$ConditionObject.awaitNanos(AbstractQueuedSynchronizer.java:2078)
	at java.util.concurrent.ScheduledThreadPoolExecutor$DelayedWorkQueue.take(ScheduledThreadPoolExecutor.java:1093)
	at java.util.concurrent.ScheduledThreadPoolExecutor$DelayedWorkQueue.take(ScheduledThreadPoolExecutor.java:809)
	at java.util.concurrent.ThreadPoolExecutor.getTask(ThreadPoolExecutor.java:1067)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1127)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"GC Daemon" #70 daemon prio=2 os_prio=0 tid=0x00007fc1cc090800 nid=0x2685 in Object.wait() [0x00007fc13d310000]
   java.lang.Thread.State: TIMED_WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at sun.misc.GC$Daemon.run(GC.java:117)
	- locked <0x00000000e3ab86c0> (a sun.misc.GC$LatencyLock)

   Locked ownable synchronizers:
	- None

"RMI Reaper" #69 prio=4 os_prio=0 tid=0x00007fc1cc065000 nid=0x2684 in Object.wait() [0x00007fc13d411000]
   java.lang.Thread.State: WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:143)
	- locked <0x00000000e3ab86d8> (a java.lang.ref.ReferenceQueue$Lock)
	at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:164)
	at sun.rmi.transport.ObjectTable$Reaper.run(ObjectTable.java:351)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"RMI TCP Accept-0" #68 daemon prio=4 os_prio=0 tid=0x00007fc1cc063800 nid=0x2683 runnable [0x00007fc13f31b000]
   java.lang.Thread.State: RUNNABLE
	at java.net.PlainSocketImpl.socketAccept(Native Method)
	at java.net.AbstractPlainSocketImpl.accept(AbstractPlainSocketImpl.java:409)
	at java.net.ServerSocket.implAccept(ServerSocket.java:545)
	at java.net.ServerSocket.accept(ServerSocket.java:513)
	at sun.rmi.transport.tcp.TCPTransport$AcceptLoop.executeAcceptLoop(TCPTransport.java:400)
	at sun.rmi.transport.tcp.TCPTransport$AcceptLoop.run(TCPTransport.java:372)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"BaseDataReader: error stream of java" #67 daemon prio=4 os_prio=0 tid=0x00007fc1b0038000 nid=0x2674 in Object.wait() [0x00007fc13e713000]
   java.lang.Thread.State: TIMED_WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at com.intellij.util.io.BaseDataReader.doRun(BaseDataReader.java:175)
	- locked <0x00000000e3f5c898> (a java.lang.Object)
	at com.intellij.util.io.BaseDataReader$1$1.run(BaseDataReader.java:66)
	at com.intellij.util.ConcurrencyUtil.runUnderThreadName(ConcurrencyUtil.java:229)
	at com.intellij.util.io.BaseDataReader$1.run(BaseDataReader.java:63)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e3ef8f48> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"BaseDataReader: output stream of java" #66 daemon prio=4 os_prio=0 tid=0x00007fc1b0036800 nid=0x2672 in Object.wait() [0x00007fc13e814000]
   java.lang.Thread.State: TIMED_WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at com.intellij.util.io.BaseDataReader.doRun(BaseDataReader.java:175)
	- locked <0x00000000e3febc98> (a java.lang.Object)
	at com.intellij.util.io.BaseDataReader$1$1.run(BaseDataReader.java:66)
	at com.intellij.util.ConcurrencyUtil.runUnderThreadName(ConcurrencyUtil.java:229)
	at com.intellij.util.io.BaseDataReader$1.run(BaseDataReader.java:63)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e3dd3568> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"java" #65 daemon prio=4 os_prio=0 tid=0x00007fc1b0034800 nid=0x2671 in Object.wait() [0x00007fc13e915000]
   java.lang.Thread.State: WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.lang.Object.wait(Object.java:502)
	at java.lang.UNIXProcess.waitFor(UNIXProcess.java:395)
	- locked <0x00000000e4ce45e8> (a java.lang.UNIXProcess)
	at com.intellij.execution.process.ProcessWaitFor$1$1.run(ProcessWaitFor.java:52)
	at com.intellij.util.ConcurrencyUtil.runUnderThreadName(ConcurrencyUtil.java:229)
	at com.intellij.execution.process.ProcessWaitFor$1.run(ProcessWaitFor.java:45)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e3dd3598> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"process reaper" #64 daemon prio=10 os_prio=0 tid=0x00007fc1b0033800 nid=0x2670 runnable [0x00007fc1c874e000]
   java.lang.Thread.State: RUNNABLE
	at java.lang.UNIXProcess.waitForProcessExit(Native Method)
	at java.lang.UNIXProcess.lambda$initStreams$3(UNIXProcess.java:289)
	at java.lang.UNIXProcess$$Lambda$14/1374542738.run(Unknown Source)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e3ef8f78> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"BaseDataReader: error stream of java" #60 prio=4 os_prio=0 tid=0x00007fc1642df000 nid=0x2661 in Object.wait() [0x00007fc13f119000]
   java.lang.Thread.State: TIMED_WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at com.intellij.util.io.BaseDataReader.doRun(BaseDataReader.java:175)
	- locked <0x00000000e0d40f60> (a java.lang.Object)
	at com.intellij.util.io.BaseDataReader$1$1.run(BaseDataReader.java:66)
	at com.intellij.util.ConcurrencyUtil.runUnderThreadName(ConcurrencyUtil.java:229)
	at com.intellij.util.io.BaseDataReader$1.run(BaseDataReader.java:63)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e3d40bd8> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"BaseDataReader: output stream of java" #59 prio=4 os_prio=0 tid=0x00007fc1642dd800 nid=0x265f in Object.wait() [0x00007fc13f21a000]
   java.lang.Thread.State: TIMED_WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at com.intellij.util.io.BaseDataReader.doRun(BaseDataReader.java:175)
	- locked <0x00000000e0d41440> (a java.lang.Object)
	at com.intellij.util.io.BaseDataReader$1$1.run(BaseDataReader.java:66)
	at com.intellij.util.ConcurrencyUtil.runUnderThreadName(ConcurrencyUtil.java:229)
	at com.intellij.util.io.BaseDataReader$1.run(BaseDataReader.java:63)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e3d40c08> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"java" #58 prio=4 os_prio=0 tid=0x00007fc1642dc800 nid=0x265d in Object.wait() [0x00007fc13f41c000]
   java.lang.Thread.State: WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.lang.Object.wait(Object.java:502)
	at java.lang.UNIXProcess.waitFor(UNIXProcess.java:395)
	- locked <0x00000000e3ed22e0> (a java.lang.UNIXProcess)
	at com.intellij.execution.process.ProcessWaitFor$1$1.run(ProcessWaitFor.java:52)
	at com.intellij.util.ConcurrencyUtil.runUnderThreadName(ConcurrencyUtil.java:229)
	at com.intellij.execution.process.ProcessWaitFor$1.run(ProcessWaitFor.java:45)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e3d40c38> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"process reaper" #57 daemon prio=10 os_prio=0 tid=0x00007fc1642dc000 nid=0x265c runnable [0x00007fc1c8787000]
   java.lang.Thread.State: RUNNABLE
	at java.lang.UNIXProcess.waitForProcessExit(Native Method)
	at java.lang.UNIXProcess.lambda$initStreams$3(UNIXProcess.java:289)
	at java.lang.UNIXProcess$$Lambda$14/1374542738.run(Unknown Source)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e3d40c68> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"BaseDataReader: error stream of java" #49 daemon prio=4 os_prio=0 tid=0x00007fc158347800 nid=0x262c runnable [0x00007fc1420fa000]
   java.lang.Thread.State: RUNNABLE
	at java.io.FileInputStream.readBytes(Native Method)
	at java.io.FileInputStream.read(FileInputStream.java:255)
	at java.io.BufferedInputStream.read1(BufferedInputStream.java:284)
	at java.io.BufferedInputStream.read(BufferedInputStream.java:345)
	- locked <0x00000000e44d4a78> (a java.lang.UNIXProcess$ProcessPipeInputStream)
	at sun.nio.cs.StreamDecoder.readBytes(StreamDecoder.java:284)
	at sun.nio.cs.StreamDecoder.implRead(StreamDecoder.java:326)
	at sun.nio.cs.StreamDecoder.read(StreamDecoder.java:178)
	- locked <0x00000000e1b93410> (a com.intellij.util.io.BaseInputStreamReader)
	at java.io.InputStreamReader.read(InputStreamReader.java:184)
	at java.io.Reader.read(Reader.java:140)
	at com.intellij.util.io.BaseOutputReader.readAvailableBlocking(BaseOutputReader.java:137)
	at com.intellij.util.io.BaseDataReader.readAvailable(BaseDataReader.java:85)
	at com.intellij.util.io.BaseDataReader.doRun(BaseDataReader.java:163)
	at com.intellij.util.io.BaseDataReader$1$1.run(BaseDataReader.java:66)
	at com.intellij.util.ConcurrencyUtil.runUnderThreadName(ConcurrencyUtil.java:229)
	at com.intellij.util.io.BaseDataReader$1.run(BaseDataReader.java:63)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e3a6e000> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"BaseDataReader: output stream of java" #48 daemon prio=4 os_prio=0 tid=0x00007fc158347000 nid=0x262a runnable [0x00007fc1421fb000]
   java.lang.Thread.State: RUNNABLE
	at java.io.FileInputStream.readBytes(Native Method)
	at java.io.FileInputStream.read(FileInputStream.java:255)
	at java.io.BufferedInputStream.read1(BufferedInputStream.java:284)
	at java.io.BufferedInputStream.read(BufferedInputStream.java:345)
	- locked <0x00000000e4ce4610> (a java.lang.UNIXProcess$ProcessPipeInputStream)
	at sun.nio.cs.StreamDecoder.readBytes(StreamDecoder.java:284)
	at sun.nio.cs.StreamDecoder.implRead(StreamDecoder.java:326)
	at sun.nio.cs.StreamDecoder.read(StreamDecoder.java:178)
	- locked <0x00000000e1ba02b8> (a com.intellij.util.io.BaseInputStreamReader)
	at java.io.InputStreamReader.read(InputStreamReader.java:184)
	at java.io.Reader.read(Reader.java:140)
	at com.intellij.util.io.BaseOutputReader.readAvailableBlocking(BaseOutputReader.java:137)
	at com.intellij.util.io.BaseDataReader.readAvailable(BaseDataReader.java:85)
	at com.intellij.util.io.BaseDataReader.doRun(BaseDataReader.java:163)
	at com.intellij.util.io.BaseDataReader$1$1.run(BaseDataReader.java:66)
	at com.intellij.util.ConcurrencyUtil.runUnderThreadName(ConcurrencyUtil.java:229)
	at com.intellij.util.io.BaseDataReader$1.run(BaseDataReader.java:63)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e3a6e060> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"java" #47 daemon prio=4 os_prio=0 tid=0x00007fc158349800 nid=0x2628 in Object.wait() [0x00007fc142cfd000]
   java.lang.Thread.State: WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.lang.Object.wait(Object.java:502)
	at java.lang.UNIXProcess.waitFor(UNIXProcess.java:395)
	- locked <0x00000000e4acbad0> (a java.lang.UNIXProcess)
	at com.intellij.execution.process.ProcessWaitFor$1$1.run(ProcessWaitFor.java:52)
	at com.intellij.util.ConcurrencyUtil.runUnderThreadName(ConcurrencyUtil.java:229)
	at com.intellij.execution.process.ProcessWaitFor$1.run(ProcessWaitFor.java:45)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e3a6e090> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"MarlinRenderer Disposer" #43 daemon prio=8 os_prio=0 tid=0x00007fc151569800 nid=0x2616 in Object.wait() [0x00007fc1496eb000]
   java.lang.Thread.State: WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:143)
	- locked <0x00000000e2787dd0> (a java.lang.ref.ReferenceQueue$Lock)
	at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:164)
	at sun.java2d.marlin.OffHeapArray$OffHeapDisposer.run(OffHeapArray.java:172)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"Batik CleanerThread" #41 daemon prio=4 os_prio=0 tid=0x00007fc14421f000 nid=0x25dd in Object.wait() [0x00007fc14a8ed000]
   java.lang.Thread.State: WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	- waiting on <0x00000000e21252b0> (a java.lang.ref.ReferenceQueue$Lock)
	at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:143)
	- locked <0x00000000e21252b0> (a java.lang.ref.ReferenceQueue$Lock)
	at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:164)
	at org.apache.batik.util.CleanerThread.run(CleanerThread.java:106)

   Locked ownable synchronizers:
	- None

"TimerQueue" #38 daemon prio=5 os_prio=0 tid=0x00007fc154007000 nid=0x25d8 waiting on condition [0x00007fc14b6f9000]
   java.lang.Thread.State: TIMED_WAITING (parking)
	at sun.misc.Unsafe.park(Native Method)
	- parking to wait for  <0x00000000e1593b70> (a java.util.concurrent.locks.AbstractQueuedSynchronizer$ConditionObject)
	at java.util.concurrent.locks.LockSupport.parkNanos(LockSupport.java:215)
	at java.util.concurrent.locks.AbstractQueuedSynchronizer$ConditionObject.awaitNanos(AbstractQueuedSynchronizer.java:2078)
	at java.util.concurrent.DelayQueue.take(DelayQueue.java:223)
	at javax.swing.TimerQueue.run(TimerQueue.java:174)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e1405958> (a java.util.concurrent.locks.ReentrantLock$NonfairSync)

"Netty Builtin Server 2" #35 prio=4 os_prio=0 tid=0x00007fc154003800 nid=0x25d5 runnable [0x00007fc14bbfc000]
   java.lang.Thread.State: RUNNABLE
	at sun.nio.ch.EPollArrayWrapper.epollWait(Native Method)
	at sun.nio.ch.EPollArrayWrapper.poll(EPollArrayWrapper.java:269)
	at sun.nio.ch.EPollSelectorImpl.doSelect(EPollSelectorImpl.java:93)
	at sun.nio.ch.SelectorImpl.lockAndDoSelect(SelectorImpl.java:86)
	- locked <0x00000000e0fb0948> (a io.netty.channel.nio.SelectedSelectionKeySet)
	- locked <0x00000000e0fb09c0> (a java.util.Collections$UnmodifiableSet)
	- locked <0x00000000e13b5fa0> (a sun.nio.ch.EPollSelectorImpl)
	at sun.nio.ch.SelectorImpl.select(SelectorImpl.java:97)
	at io.netty.channel.nio.SelectedSelectionKeySetSelector.select(SelectedSelectionKeySetSelector.java:62)
	at io.netty.channel.nio.NioEventLoop.select(NioEventLoop.java:756)
	at io.netty.channel.nio.NioEventLoop.run(NioEventLoop.java:411)
	at io.netty.util.concurrent.SingleThreadEventExecutor$5.run(SingleThreadEventExecutor.java:884)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"process reaper" #29 daemon prio=10 os_prio=0 tid=0x00007fc1509a5800 nid=0x25ce runnable [0x00007fc160c26000]
   java.lang.Thread.State: RUNNABLE
	at java.lang.UNIXProcess.waitForProcessExit(Native Method)
	at java.lang.UNIXProcess.lambda$initStreams$3(UNIXProcess.java:289)
	at java.lang.UNIXProcess$$Lambda$14/1374542738.run(Unknown Source)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e0c56788> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"BaseDataReader: error stream of fsnotifier64" #28 prio=4 os_prio=0 tid=0x00007fc15098a000 nid=0x25cc runnable [0x00007fc160d3a000]
   java.lang.Thread.State: RUNNABLE
	at java.io.FileInputStream.readBytes(Native Method)
	at java.io.FileInputStream.read(FileInputStream.java:255)
	at java.io.BufferedInputStream.read1(BufferedInputStream.java:284)
	at java.io.BufferedInputStream.read(BufferedInputStream.java:345)
	- locked <0x00000000e2b6b8f8> (a java.lang.UNIXProcess$ProcessPipeInputStream)
	at sun.nio.cs.StreamDecoder.readBytes(StreamDecoder.java:284)
	at sun.nio.cs.StreamDecoder.implRead(StreamDecoder.java:326)
	at sun.nio.cs.StreamDecoder.read(StreamDecoder.java:178)
	- locked <0x00000000e2ed5190> (a com.intellij.util.io.BaseInputStreamReader)
	at java.io.InputStreamReader.read(InputStreamReader.java:184)
	at java.io.Reader.read(Reader.java:140)
	at com.intellij.util.io.BaseOutputReader.readAvailableBlocking(BaseOutputReader.java:137)
	at com.intellij.util.io.BaseDataReader.readAvailable(BaseDataReader.java:85)
	at com.intellij.util.io.BaseDataReader.doRun(BaseDataReader.java:163)
	at com.intellij.util.io.BaseDataReader$1$1.run(BaseDataReader.java:66)
	at com.intellij.util.ConcurrencyUtil.runUnderThreadName(ConcurrencyUtil.java:229)
	at com.intellij.util.io.BaseDataReader$1.run(BaseDataReader.java:63)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e0c567b8> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"BaseDataReader: output stream of fsnotifier64" #27 prio=4 os_prio=0 tid=0x00007fc150989800 nid=0x25cb runnable [0x00007fc160e3b000]
   java.lang.Thread.State: RUNNABLE
	at java.io.FileInputStream.readBytes(Native Method)
	at java.io.FileInputStream.read(FileInputStream.java:255)
	at java.io.BufferedInputStream.read1(BufferedInputStream.java:284)
	at java.io.BufferedInputStream.read(BufferedInputStream.java:345)
	- locked <0x00000000e2b6b8d0> (a java.lang.UNIXProcess$ProcessPipeInputStream)
	at sun.nio.cs.StreamDecoder.readBytes(StreamDecoder.java:284)
	at sun.nio.cs.StreamDecoder.implRead(StreamDecoder.java:326)
	at sun.nio.cs.StreamDecoder.read(StreamDecoder.java:178)
	- locked <0x00000000e0c68ba0> (a com.intellij.util.io.BaseInputStreamReader)
	at java.io.InputStreamReader.read(InputStreamReader.java:184)
	at java.io.Reader.read(Reader.java:140)
	at com.intellij.util.io.BaseOutputReader.readAvailableBlocking(BaseOutputReader.java:137)
	at com.intellij.util.io.BaseDataReader.readAvailable(BaseDataReader.java:85)
	at com.intellij.util.io.BaseDataReader.doRun(BaseDataReader.java:163)
	at com.intellij.util.io.BaseDataReader$1$1.run(BaseDataReader.java:66)
	at com.intellij.util.ConcurrencyUtil.runUnderThreadName(ConcurrencyUtil.java:229)
	at com.intellij.util.io.BaseDataReader$1.run(BaseDataReader.java:63)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e0c6c768> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"fsnotifier64" #26 prio=4 os_prio=0 tid=0x00007fc150987800 nid=0x25ca in Object.wait() [0x00007fc1637fd000]
   java.lang.Thread.State: WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	- waiting on <0x00000000e2c45ee0> (a java.lang.UNIXProcess)
	at java.lang.Object.wait(Object.java:502)
	at java.lang.UNIXProcess.waitFor(UNIXProcess.java:395)
	- locked <0x00000000e2c45ee0> (a java.lang.UNIXProcess)
	at com.intellij.execution.process.ProcessWaitFor$1$1.run(ProcessWaitFor.java:52)
	at com.intellij.util.ConcurrencyUtil.runUnderThreadName(ConcurrencyUtil.java:229)
	at com.intellij.execution.process.ProcessWaitFor$1.run(ProcessWaitFor.java:45)
	at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e2c91d48> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"Periodic tasks thread" #25 daemon prio=6 os_prio=0 tid=0x00007fc15000f000 nid=0x25c7 runnable [0x00007fc1c8235000]
   java.lang.Thread.State: TIMED_WAITING (parking)
	at sun.misc.Unsafe.park(Native Method)
	- parking to wait for  <0x00000000e12d1aa0> (a java.util.concurrent.locks.AbstractQueuedSynchronizer$ConditionObject)
	at java.util.concurrent.locks.LockSupport.parkNanos(LockSupport.java:215)
	at java.util.concurrent.locks.AbstractQueuedSynchronizer$ConditionObject.awaitNanos(AbstractQueuedSynchronizer.java:2078)
	at java.util.concurrent.DelayQueue.take(DelayQueue.java:223)
	at com.intellij.util.concurrency.AppDelayQueue$1.run(AppDelayQueue.java:43)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"AWT-EventQueue-0" #23 prio=6 os_prio=0 tid=0x00007fc19083d800 nid=0x25c6 waiting on condition [0x00007fc1636fc000]
   java.lang.Thread.State: WAITING (parking)
	at sun.misc.Unsafe.park(Native Method)
	- parking to wait for  <0x00000000e1a38020> (a java.util.concurrent.locks.AbstractQueuedSynchronizer$ConditionObject)
	at java.util.concurrent.locks.LockSupport.park(LockSupport.java:175)
	at java.util.concurrent.locks.AbstractQueuedSynchronizer$ConditionObject.await(AbstractQueuedSynchronizer.java:2039)
	at java.awt.EventQueue.getNextEvent(EventQueue.java:560)
	at com.intellij.ide.IdeEventQueue.getNextEvent(IdeEventQueue.java:473)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:170)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:116)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:105)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:101)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:93)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:82)

   Locked ownable synchronizers:
	- None

"AWT-Shutdown" #24 prio=5 os_prio=0 tid=0x00007fc19083c000 nid=0x25c5 in Object.wait() [0x00007fc172717000]
   java.lang.Thread.State: WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.lang.Object.wait(Object.java:502)
	at sun.awt.AWTAutoShutdown.run(AWTAutoShutdown.java:295)
	- locked <0x00000000e1c140b8> (a java.lang.Object)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"Timer-0" #21 daemon prio=5 os_prio=0 tid=0x00007fc190805000 nid=0x25c4 in Object.wait() [0x00007fc172818000]
   java.lang.Thread.State: TIMED_WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.util.TimerThread.mainLoop(Timer.java:552)
	- locked <0x00000000e1c35480> (a java.util.TaskQueue)
	at java.util.TimerThread.run(Timer.java:505)

   Locked ownable synchronizers:
	- None

"Netty Builtin Server 1" #17 prio=5 os_prio=0 tid=0x00007fc190529800 nid=0x25bd runnable [0x00007fc1952d3000]
   java.lang.Thread.State: RUNNABLE
	at sun.nio.ch.EPollArrayWrapper.epollWait(Native Method)
	at sun.nio.ch.EPollArrayWrapper.poll(EPollArrayWrapper.java:269)
	at sun.nio.ch.EPollSelectorImpl.doSelect(EPollSelectorImpl.java:93)
	at sun.nio.ch.SelectorImpl.lockAndDoSelect(SelectorImpl.java:86)
	- locked <0x00000000e1a30000> (a io.netty.channel.nio.SelectedSelectionKeySet)
	- locked <0x00000000e1a30018> (a java.util.Collections$UnmodifiableSet)
	- locked <0x00000000e1a34778> (a sun.nio.ch.EPollSelectorImpl)
	at sun.nio.ch.SelectorImpl.select(SelectorImpl.java:97)
	at io.netty.channel.nio.SelectedSelectionKeySetSelector.select(SelectedSelectionKeySetSelector.java:62)
	at io.netty.channel.nio.NioEventLoop.select(NioEventLoop.java:756)
	at io.netty.channel.nio.NioEventLoop.run(NioEventLoop.java:411)
	at io.netty.util.concurrent.SingleThreadEventExecutor$5.run(SingleThreadEventExecutor.java:884)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"ObjectCleanerThread" #16 daemon prio=1 os_prio=0 tid=0x00007fc190527800 nid=0x25bc in Object.wait() [0x00007fc1953d4000]
   java.lang.Thread.State: TIMED_WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:143)
	- locked <0x00000000e0c5bee0> (a java.lang.ref.ReferenceQueue$Lock)
	at io.netty.util.internal.ObjectCleaner$1.run(ObjectCleaner.java:54)
	at io.netty.util.concurrent.FastThreadLocalRunnable.run(FastThreadLocalRunnable.java:30)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"process reaper" #15 daemon prio=10 os_prio=0 tid=0x00007fc190414000 nid=0x25bb runnable [0x00007fc195612000]
   java.lang.Thread.State: RUNNABLE
	at java.lang.UNIXProcess.waitForProcessExit(Native Method)
	at java.lang.UNIXProcess.lambda$initStreams$3(UNIXProcess.java:289)
	at java.lang.UNIXProcess$$Lambda$14/1374542738.run(Unknown Source)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- <0x00000000e1a298b0> (a java.util.concurrent.ThreadPoolExecutor$Worker)

"AWT-XAWT" #14 daemon prio=6 os_prio=0 tid=0x00007fc19009f800 nid=0x25b8 runnable [0x00007fc1960b7000]
   java.lang.Thread.State: RUNNABLE
	at sun.awt.X11.XToolkit.waitForEvents(Native Method)
	at sun.awt.X11.XToolkit.run(XToolkit.java:570)
	at sun.awt.X11.XToolkit.run(XToolkit.java:534)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"Java2D Disposer" #12 daemon prio=10 os_prio=0 tid=0x00007fc190085000 nid=0x25b7 in Object.wait() [0x00007fc1c812f000]
   java.lang.Thread.State: WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:143)
	- locked <0x00000000e13ebd80> (a java.lang.ref.ReferenceQueue$Lock)
	at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:164)
	at sun.java2d.Disposer.run(Disposer.java:148)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

"DestroyJavaVM" #11 prio=5 os_prio=0 tid=0x00007fc1e800c000 nid=0x25a6 waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

   Locked ownable synchronizers:
	- None

"Service Thread" #9 daemon prio=9 os_prio=0 tid=0x00007fc1e8189000 nid=0x25b4 runnable [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

   Locked ownable synchronizers:
	- None

"C1 CompilerThread2" #8 daemon prio=9 os_prio=0 tid=0x00007fc1e817d800 nid=0x25b3 waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

   Locked ownable synchronizers:
	- None

"C2 CompilerThread1" #7 daemon prio=9 os_prio=0 tid=0x00007fc1e817b800 nid=0x25b2 waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

   Locked ownable synchronizers:
	- None

"C2 CompilerThread0" #6 daemon prio=9 os_prio=0 tid=0x00007fc1e8179800 nid=0x25b1 waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

   Locked ownable synchronizers:
	- None

"Signal Dispatcher" #5 daemon prio=9 os_prio=0 tid=0x00007fc1e8177800 nid=0x25b0 runnable [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

   Locked ownable synchronizers:
	- None

"Surrogate Locker Thread (Concurrent GC)" #4 daemon prio=9 os_prio=0 tid=0x00007fc1e8176000 nid=0x25af waiting on condition [0x0000000000000000]
   java.lang.Thread.State: RUNNABLE

   Locked ownable synchronizers:
	- None

"Finalizer" #3 daemon prio=8 os_prio=0 tid=0x00007fc1e8143000 nid=0x25ae in Object.wait() [0x00007fc1c942b000]
   java.lang.Thread.State: WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:143)
	- locked <0x00000000e0cd9e98> (a java.lang.ref.ReferenceQueue$Lock)
	at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:164)
	at java.lang.ref.Finalizer$FinalizerThread.run(Finalizer.java:209)

   Locked ownable synchronizers:
	- None

"Reference Handler" #2 daemon prio=10 os_prio=0 tid=0x00007fc1e813e800 nid=0x25ad in Object.wait() [0x00007fc1c952c000]
   java.lang.Thread.State: WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.lang.Object.wait(Object.java:502)
	at java.lang.ref.Reference.tryHandlePending(Reference.java:191)
	- locked <0x00000000e0cfcc00> (a java.lang.ref.Reference$Lock)
	at java.lang.ref.Reference$ReferenceHandler.run(Reference.java:153)

   Locked ownable synchronizers:
	- None

"VM Thread" os_prio=0 tid=0x00007fc1e8137000 nid=0x25ac runnable 

"Gang worker#0 (Parallel GC Threads)" os_prio=0 tid=0x00007fc1e8012800 nid=0x25a7 runnable 

"Gang worker#1 (Parallel GC Threads)" os_prio=0 tid=0x00007fc1e801f000 nid=0x25a8 runnable 

"Gang worker#2 (Parallel GC Threads)" os_prio=0 tid=0x00007fc1e8020800 nid=0x25a9 runnable 

"Gang worker#3 (Parallel GC Threads)" os_prio=0 tid=0x00007fc1e8022800 nid=0x25aa runnable 

"Concurrent Mark-Sweep GC Thread" os_prio=0 tid=0x00007fc1e8065800 nid=0x25ab runnable 

"VM Periodic Task Thread" os_prio=0 tid=0x00007fc1e818b800 nid=0x25b5 waiting on condition 

JNI global references: 7414
```


There can be following thread states ::

*NEW: The thread is created but has not been processed yet.
*RUNNABLE: The thread is occupying the CPU and processing a task. (It may be in WAITING status due to the OS's resource distribution.)
*BLOCKED: The thread is waiting for a different thread to release its lock in order to get the monitor lock.
*WAITING: The thread is waiting by using a wait, join or park method.
*TIMED_WAITING: The thread is waiting by using a sleep, wait, join or park method. (The difference from WAITING is that the maximum waiting time is specified by the method parameter, and WAITING can be relieved by time as well as external changes.) 



[Thread Analysis] (https://dzone.com/articles/how-analyze-java-thread-dumps)

