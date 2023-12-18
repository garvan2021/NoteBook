# Python
## Fastapi

### How to return a response with image from an ndarray?
https://stackoverflow.com/questions/71595635/render-numpy-array-in-fastapi/71639658#71639658

## Uvicorn

### What happend when the uvicorn start a server?
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