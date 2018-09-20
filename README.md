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
	- <0x00000000e293bfe8> (a java.util.concurrent.ThreadPoolExecutor$Worker)s

"RMI RenewClean-[127.0.0.1:44621]" #72 daemon prio=4 os_prio=0 tid=0x00007fc1a8140800 nid=0x2689 in Object.wait() [0x00007fc13d10e000]
   java.lang.Thread.State: TIMED_WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:143)
	- locked <0x00000000e3ab8690> (a java.lang.ref.ReferenceQueue$Lock)
	at sun.rmi.transport.DGCClient$EndpointEntry$RenewCleanThread.run(DGCClient.java:553)
	at java.lang.Thread.run(Thread.java:745)

   Locked ownable synchronizers:
	- None

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


"Timer-0" #21 daemon prio=5 os_prio=0 tid=0x00007fc190805000 nid=0x25c4 in Object.wait() [0x00007fc172818000]
   java.lang.Thread.State: TIMED_WAITING (on object monitor)
	at java.lang.Object.wait(Native Method)
	at java.util.TimerThread.mainLoop(Timer.java:552)
	- locked <0x00000000e1c35480> (a java.util.TaskQueue)
	at java.util.TimerThread.run(Timer.java:505)

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

* NEW: The thread is created but has not been processed yet.
* RUNNABLE: The thread is occupying the CPU and processing a task. (It may be in WAITING status due to the OS's resource distribution.)
* BLOCKED: The thread is waiting for a different thread to release its lock in order to get the monitor lock.
* WAITING: The thread is waiting by using a wait, join or park method.
* TIMED_WAITING: The thread is waiting by using a sleep, wait, join or park method. (The difference from WAITING is that the maximum waiting time is specified by the method parameter, and WAITING can be relieved by time as well as external changes.) 



[Thread Analysis](https://dzone.com/articles/how-analyze-java-thread-dumps)

