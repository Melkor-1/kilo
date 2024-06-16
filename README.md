# Kilo (Work Under Progress)

[![build](https://github.com/Melkor-1/kilo/actions/workflows/ci.yml/badge.svg)](https://github.com/Melkor-1/kilo/actions/workflows/ci.yml?event=push)
[![License](https://img.shields.io/badge/license-BSDv2-blue.svg)](https://https://github.com/Melkor-1/kilo/edit/main/LICENSE)

## A Text Editor with Lexical Highlight and Search 

kilo is modelled after [Antirez's kilo](https://github.com/antirez/kilo), but with a focus on robustness 
instead of being featureful:

1. It is written in C23, and compiles cleanly with a strict set of warnings.
2. The code has been broken down into resuable and different files, separating concerns and making the
   code easier to test.
3. There are no known memory leaks. The program runs cleanly under valgrind.
4. There are no known memory bugs.
5. There is no global state. A `struct` containing all the state is passed around to the functions that require it.
6. The editor has unit tests.
7. Saving a file is a more robust process. When saving, the editor prompts for a filename and checks if the file
   already exists, asking the user for confirmation to overwrite if necessary. When a file is opened via a
   command-line argument, the editor checks if the file's timestamp has changed since it was last accessed and
   prompts the user to save any changes if the file has been modified.
8. The editor recognizes and highlights all C23 symbols.

## Future directions

1. Store a single copy of each line, and generate the display version only when needed. The "original" kilo actually
   stores 2 copies of each line: one is the contents of the line as they appear in the file, and the other is as
   they appear on the screen.
2. Keep track of which lines have changed since they were last drawn, and only redraw those that have changed. The
   original kilo redraws the screen after every keypress.
3. To better ensure data is saved properly, create a backup of the file and rename the backup to the original file.
   The original kilo writes directly to the current file, which is prone to data loss; if an error occurs whilst
   writing to the file, there is no way to recover the partially overwritten file back to its original form.
4. Ensure that the editor compiles cleanly and works correctly on Linux, FreeBSD, OpenBSD, NetBSD, MacOS,
   Oracle Solaris, and OmniOS.
