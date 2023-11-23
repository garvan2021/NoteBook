# python

## interpreter bug -- readline 

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