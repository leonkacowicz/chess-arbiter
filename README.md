# What is this?
This package is a one of a series packages intended to
support the development of general purpose chess engines and tools.

This package implements a chess-arbiter, an executable that executes 
2 UCI-compatible chess engines and makes them play against each other.

This chess-arbiter supports several features, such as determining individual
process priorities for each of the engines, limiting the search depth,
move time and total time for each of the engines. 

# How do I build it?

This package uses CMake as a build-tool. In theory, it requires CMake 3.5,
but I haven't tested it with previous versions of CMake. If you manage to
build it with an older version of CMake, let me know or send a pull request
decreasing the required version on line 1 of `/CMakeLists.txt`

To build it:
```sh
mkdir build
cd build
cmake ..
make
```

# Testing
After building, an executable at `build/test/arbiter/arbiter_test` should be generated.
All tests specified in `/tests/` should be invoked by this executable.

# How do I invoke the arbiter?

To invoke the arbiter, use the command line options as explained below:

```text
  -h [ --help ]                   print usage message
  --white-exec arg                [REQUIRED] path to engine executable that 
                                  will play with white pieces
  --white-input arg               path to white options input file
  --white-init-time arg (=0)      initial time for white in milliseconds
  --white-move-time arg (=0)      move time for white in milliseconds
  --white-max-depth arg (=0)      max depth for white in plys
  --white-time-increment arg (=0) time increment per move for white in 
                                  milliseconds
  --white-priority arg (=0)       white engine process priority ('nice' value)
  --black-exec arg                [REQUIRED] path to engine executable that 
                                  will play with black pieces
  --black-input arg               path to black options input file
  --black-init-time arg (=0)      initial time for black in milliseconds
  --black-move-time arg (=0)      move time for white in milliseconds
  --black-max-depth arg (=0)      max depth for black in plys
  --black-time-increment arg (=0) time increment per move for black in 
                                  milliseconds
  --black-priority arg (=0)       black engine process priority ('nice' value)
  --output arg                    location of pgn output file
  --initial-pos arg (=startpos)   string representing initial position either 
                                  as 'startpos moves e2e4 e7e5 ...' or as 'fen 
                                  fen-value moves m1 m2'
  --verbose                       enables verbose mode
```