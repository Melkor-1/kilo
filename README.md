# kilo

A Text Editor with Lexical Highlight and Search

kilo is modelled after [Antirez's kilo](https://github.com/antirez/kilo), but with a focus on robustness instead of being featureful:

1. It is written in C23, and compiles cleanly with a strict set of warnings.
2. The code has been broken down into resuable and different files, separating concerns and making the code easier to test.
3. There are no memory leaks. The program runs cleanly under valgrind.
4. There is no global state. A `struct` containing all the state is passed around to the functions that require it.
5. The editor has unit tests.
6. Saving a file is a more robust process. When saving, the editor prompts for a filename and checks if the file already exists, asking the user for confirmation to overwrite if necessary. When a file is opened via a command-line argument, the editor checks if the file's timestamp has changed since it was last accessed and prompts the user to save any changes if the file has been modified.
7. The editor recognizes and highlights all C23 symbols.
