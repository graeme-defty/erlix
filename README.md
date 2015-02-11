# erlix
Assistance in converting erlang source to elixir

Erlix
=====

AS A START point in learning Elixir I decided to try to convert an existing
project from erlang to elixir (jaderl -> jadelix).  I quickly realised that there was
a huge amount of grunt editing needed.
After manunally completing 3 one-line functions and their tests I was already going crazy
from the grinding repetitiveness (is that a word? Repetetivity?) of it all.

I also realised that all this horrible drudgery was going to take an age.

This is what computers are good at!

I decided that I needed to take a step back and that my first work in Elixir
should be to create a simple program to do some of more obvious and repetetive tasks
before I started to look at changing the code by hand.

ERLIX IS that program. It knows virtually nothing about the structure of Erlang programs,
and operates in a very simple-minded way, just scanning the text looking for special characters and
a (very) few special constructs to transform the input code.

(In truth it is a fairly nasty piece of work, operating purely on the program source code and doing dumb textual replacements, but it did enough to make my job a bit easier, and served its primary purpose, which was to get me through my first fumbling steps with elixir.)

The resultant output:
	- still needs to be converted to 'real' elixir by hand
	- does not take any advantage of all the great features of elixir

What it does
------------
	- changes "%" to "#" at the start of comments
	- changes -define to defmacro for macro definitions
	- changes macro names to all lower case
	- changes macro usages to match the new names
	- changes the ?_assertEqual macro to be a plain 'assert'
	- adjusts variable names to be lower case
	- adjusts atom names to add a ':' (both quoted and unquoted atoms)
	- changes '$x' character literals to '?x'
	- changes '=<' to '<='
	- changes '->', ';' and '.' to 'do', 'end' and 'end' respectively

What it does not
----------------
This list is indeed long. Basically, apart from the relatively simple character transformations
listed above, you are on your own. Erlix has no knowledge of the structure of erlang programs
but nevertheless provides a useful first pass and does save a LOT of typing.

One aspect to which I have given no consideration is that erlix could be biassed to my style
of erlang programming, which may be atypical. Caveat emptor!

There are a hundred different ways this could be improved, and I would be happy to incorporate any changes/improvements I get, but it has served its purpose for me and I do not plan to work on it further myself.

The correct way to do this job would probably be to use the erlang compile functions to build an erlang AST and then walk that, spitting out elixr as you go. I didnt have clear enough knowledge of the erlang AST and find the functions supporting it (parse etc.) complex and confusing, and didnt have time to learn all I needed to go that way, so this is what I used.

In summary, this may help you, it may not. 
