# Cli Tools

Tools for quickly creating Command Line Interface scripts with Python.

[![Build Status](https://travis-ci.org/rshk/clitools.png)](https://travis-ci.org/rshk/clitools)


## Example

```python
#!/usr/bin/env python

from clitools import CliApp

cli = CliApp()

@cli.command
def hello(args):
    print "Hello, world!"

@cli.command
@cli.arg('--name')
@cli.flag('--bye')
def hello2(args):
    greeting = "Bye" if args.bye else "Hello"
    message = "{0}, {1}!".format(greeting, args.name or 'Mr.X')
    print(message)

if __name__ == '__main__':
    cli.run()
```

### Running the example

```console
% ./simple_app.py
usage: cli-app [-h] {hello,hello2} ...
cli-app: error: too few arguments

% ./simple_app.py hello
Hello, world!

% ./simple_app.py hello --help
usage: cli-app hello [-h]

optional arguments:
  -h, --help  show this help message and exit

% ./simple_app.py hello2
Hello, Mr.X!

% ./simple_app.py hello2 --help
usage: cli-app hello2 [-h] [--name NAME] [--bye]

optional arguments:
  -h, --help   show this help message and exit
  --name NAME
  --bye

% ./simple_app.py hello2 --name=world
Hello, world!

% ./simple_app.py hello2 --name=world --bye
Bye, world!
```
