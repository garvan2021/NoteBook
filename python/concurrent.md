# Python
## threading.Thread

- When you want to use `Thread` class to do some thread-relating work, you can initialze `Thread` class by customize arguments and use `Thread.start()` to let the job start running, and make sure you should override `Thread.run()` instead of directly invoke

## queue.Queue

- When Queue is initialized, the `unfinished_tasks` is also set to be `0`, it would keep increased when `put` method is invoked, but it do not decresed when `get` method is invoked on contrary. The only way to make it decreasing is to invoke `task_done` from outside
