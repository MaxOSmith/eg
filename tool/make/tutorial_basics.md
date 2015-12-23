Makefiles are convenient way to organize code compilation. It allows you to refer to very large complicated build processes with very simple and short code calls. To exemplify, we're going to consider the canonical "Hello World" program.

```
// main.cpp
#include <iostream>

int main() {
    std::cout << "Hello World!" << std::endl;
}
```

To compile this program you would run (here $ denotes terminal commands):

```
$ g++ main.cpp -o main
```

Now, this seems rather easy. There's not a whole lot of trouble re-typing this each time you need to re-build the program. Just to make things more interesting, lets consider the EECS 280 case where we require a whole ton of flags to make sure that any potential errors are caught earlier:

```$ g++ -pedantic -Wall -Werror -O1 main.cpp -o main```

This would definitely be awful to have to type every time we wanted to make rebuild the program. That's where Makefiles come in! Makefiles allow us to create a sort-of function call that would run these command line compilations for us.

We're going to define a function called "build," so that when we wish to build our program it's only a simple bash command like:

```$ make build```

You'll notice that make wants to know which build command to run, so you need to specify it as the first command line argument. Namely,

```$ make <build_function>```

So now we need to actually implement this function. Makefiles are conveniently always named "Makefile" so we create our Makefile file called Makefile (really fun to say outloud). And we can add build commands with the following syntax, note here that <> represent an abstraction, and they're actually not needed:
```
<commandName>:	<dependencies>
		<bashCommand0>
		<...>
		<bashCommandN>
```

* *commandName*: the name of the command you want to build
* *dependencies*: a space separated list of dependent files, when these files change it knows that it needs to be re-built
* *bashCommand*: a list of all the terminal commands you want run when commandName is run

For our "Hello World!" example, we are dependent on our main.cpp file, so we add it to the list of our dependencies. We specified our commandName as "build," and also described our bash commands earlier. This allows us to write our Makefile as so (please note that '#' are considered comment lines in Makefiles):

```
# Makefile

build: main.cpp
       g++ -pedantic -Wall -Werror -O1 main.cpp -o main
       Now we can very easily build our project by running:
       $ make build
```

