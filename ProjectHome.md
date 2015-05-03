**SEE MY NEW LP GENERAL TOOL: http://code.google.com/p/nano-lp**

Small (~800Kb) Literate Programming Tool


---

# TCLP - Literate Programming (LP) System #

---


## What is the LP? ##

From http://en.wikipedia.org/wiki/Literate_programming:

"...Literate programming is an approach to programming introduced by Donald
Knuth as an alternative to the structured programming paradigm of the 1970s.
The literate programming paradigm, as conceived by Knuth, represents a move
away from writing programs in the manner and order imposed by the computer, and
instead enables programmers to develop programs in the order demanded by the
logic and flow of their thoughts. Literate programs are written as an
uninterrupted exposition of logic in an ordinary human language, much like the
text of an essay, in which macros are included to hide abstractions and
traditional source code..."

See more: http://www.literateprogramming.com

## What is it for me? ##

Approach to create supportable, readable code (not only by author but also
by another programmers). Code in LP is more "live", it's life is longer,
any programmer can read and understand it, because not program is not only
code with included comments (sometimes), but it's like book or article:
with special formatting, with tables, with figures, images, references
and more...

## What is the difference between D. Knuth LP approach and TCLP? ##

Mr. Knuth uses named "chunks" of code. IMHO any code transformation is deal of
programming language or similar tools - not of LP tool. So in TCLP there are not
any code transformation - it's tool for create flexible documentation for
source code and write program in the same place in the one time. Generated
(woven) "documentation" is rich, has autocreate references and so on.

## How TCLP works ##

TCLP is a very small command line utility. You write one file with documentation
and code chunks then run TCLP tool to get output HTML file for documentation and
different source code files (one TCLP source can generate any number of output
code files). Generated HTML document is UTF-8 encoded.
If you use Starpack, run:
tclp -h
If you use tclkit then run:
tclkit main.tcl -h

## How to install ##

Unpack somewhere tcp-win-xx.zip and setup system paths to this place. If you
use Unix-like system then unpack tclp-src-xx.zip somewhere and use Tclkit
or Tclsh but with IncrTcl.

## Dependences ##

If you are Linux user, you need Tcl interpreter and IncrTcl package. For
Windows users nothing special is needed.

## What is the language of TCLP sources? ##

It based on Tcl (it's real Tcl and run code in safe/restricted Tcl-interpreter,
so user has only limited commands. To run any Tcl command it's possible to use
special command 'unsafe'.
Actually, TCLP is StarKit (created with tclkit). So sources are available :)

## How this looks? ##

See 'test.html' for examples of markup and code generation.

## TCLP concepts ##

```
LP src -> HTML-doc (automatically)
       -> src-file 1 (by hand with command 'putcode' in 'atend' body)
       -> ...
```

## TCLP features ##

1. Document has 'document header' with fields: TITLE, PROJECT, VERSION,
DESCRIPTION, AUTHOR, ADDRESS, TAGS, it shown on the top of document.

2. User can define values of this fields (and any other field) and can use
defined fields in the document body (even in code chunks). There are special
fields: APPNAME, APPVERSION, TIMESTAMP, DATE, TIME.

3. Document has auto-generated TOC (table-of-contents), IT (index-table),
ERT (external-references-table).
TOC is placed in the start of the document. IT is placed at the end of document.
ERT is placed last.

4. TOC is generated automatically for all headers, defined with 'head' command.

5. IT is generated automatically for all code chunks and includes file names of
output chunks and lines numbers where to find them.

6. ERT is generated automatically for all external references in the document,
defined with 'ref' command and includes back-references to it's usage in the
document body.

7. Markup commands includes commands for bold, underlined, italic and monotyped
text. Top/bottom indexes are supported also. Markups can be nested.

8. There is special file with abbreviations to be used in section names and
acronyms also.

9. User can use acronym in the text from abbreviations file or explicitly with
embedded expansion.

10. User can create "vocabularies" - tables of definitions - from abbreviations
file or embedded, defined explicitly.

11. There are named counters (auto-incremented) to use in captions and so on.

12. Code chunks are special formatted fragments of source code with lines
numbering, optional syntax highlighting (only keywords). Lines can be numbered
in continuously manner (with the same counter names) or in independent.
User can reference to code lines by chunk name (section) and line number or
with defining NAME of code line and usage of this name for referencing.

13. Tables are supported: with attributes (table/row/cell), spanning, nesting.

14. Lists (ordered/unordered) are also supported: with attributes; they can be
nested also.

15. User can insert image with 'embed' command. Any fragment of document can be
"framed" with 'frame' command. It creates frame with caption (on top/on bottom),
name and links (for referencing).

16. There are 2 kinds of citations: inlined and blocked. Citation can have linked
URL (shown as "More...")

17. User can insert in document text any previous defined field values, but also
variables from environment. Special environment variables is the USER - this is
the name of user running tool.

18. There is a special command 'wrap' for wrapping text with any word or quotation
symbols, braces, etc.

19. There is a command 'ent' to translate special symbols to HTML entities.

20. There are references:
  * to external URL
  * to header
  * to line of code chunk/named line of code chunk
  * to code chunk
  * to frames
  * to any place of document where user defines own link

21. There are 2 special commands: 'atstart', 'atend'. Mainly used is 'atend'
for code generation from code chunks. User can define there what code chunks
to be written to output source files (by sections, by glob-pattern of sections).
Also is possible to write any free text to output file.

22. Most of created HTML tags has CSS-classes. For all available CSS classes,
see 'tclp.css' file. Used CSS file can be defined with command line option.

23. User can add syntax keywords for any other language (for highlighting).

# Examples #

For examples see 'test.html', test.c, test.h (generated from 'test.lp'). For
information about commands, see 'commands.txt'. Each command can be used in short
form: for example, `[italic sometext]` or `[ita sometext]`. When sometext has more
then one word, { and } should be used.