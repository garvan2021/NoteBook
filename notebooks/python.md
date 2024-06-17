# Python

## Python Core

### Concurrent

#### Bytes

How to get the size of a byte
```Python
import struct
size = struct.calcsize(b"test")
```

#### threading.Thread

- When you want to use `Thread` class to do some thread-relating work, you can initialze `Thread` class by customize arguments and use `Thread.start()` to let the job start running, and make sure you should override `Thread.run()` instead of directly invoke

#### queue.Queue

- When Queue is initialized, the `unfinished_tasks` is also set to be `0`, it would keep increased when `put` method is invoked, but it do not decresed when `get` method is invoked on contrary. The only way to make it decreasing is to invoke `task_done` from outside



### Interpreter

#### readline bug

according to [interpreter](https://docs.python.org/3/tutorial/interpreter.html) document,
python support typing [ctrl-p] to retreive history command and other arrow button to do editing, 

it all depends on **GUN readline** library, its a very useful tool to do some just in time test.   

but with unknown reason, it just not working at my ubuntu machine, like when I click "up" button,   
it outputs the "^[[A" which was suppose to be history command like "exit()"

here is my solution, it may not work for you, its a simple record here.

$ conda/pip uninstall readline

for more details and further resource, you can check out below:  
[GUN readline](https://tiswww.case.edu/php/chet/readline/readline.html)
[python interpreter](https://docs.python.org/3/tutorial/interpreter.html)


## Python Third Party

### Fastapi

#### How to return a response with image from an ndarray?
https://stackoverflow.com/questions/71595635/render-numpy-array-in-fastapi/71639658#71639658

### Uvicorn

#### What happend when the uvicorn start a server?
- When the uvicorn start a server, it first load the config as follow:
    ```Python
    config = Config(app, *args, **kwargs)
    server = Server(config=config)
    ```
    this loads the `app` path which is not the truly running instance.

- then, the `uvicorn` setup the variable `_event_loop_policy` of python package `asyncio` to `uvloop.EventLoopPolicy` which looks like is a `Cython` class that designed to speed up the server executions.
    ```Python
    asyncio.set_event_loop_policy(uvloop.EventLoopPolicy())
    ```

- After the `asyncio`'s environment is ready, the `uvicorn` instantly start all the synchronize services.
    ```Python
    config.load()  # this truely instantiate app class with configs.
    await server.startup(sockets=sockets)  # this creates a TCP server which take full use of uvloop 
    ```
