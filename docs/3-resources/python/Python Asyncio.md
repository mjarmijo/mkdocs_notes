[[python]]
[[async]]
[[concurrency]]


Python’s asyncio library enables you to write concurrent code using the async and await keywords. The core building blocks of async I/O in Python are awaitable objects—most often coroutines—that an event loop schedules and executes asynchronously. This programming model lets you efficiently manage multiple I/O-bound tasks within a single thread of execution.

In this tutorial, you’ll learn how Python asyncio works, how to define and run coroutines, and when to use asynchronous programming for better performance in applications that perform I/O-bound tasks.

By the end of this tutorial, you’ll understand that:

    Python’s asyncio provides a framework for writing single-threaded concurrent code using coroutines, event loops, and non-blocking I/O operations.
    For I/O-bound tasks, async I/O can often outperform multithreading—especially when managing a large number of concurrent tasks—because it avoids the overhead of thread management.
    You should use asyncio when your application spends significant time waiting on I/O operations, such as network requests or file access, and you want to run many of these tasks concurrently without creating extra threads or processes.

https://realpython.com/async-io-python/