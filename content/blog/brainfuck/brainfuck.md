---
title: Brainfuck
date: 2020-09-10 00:00:00 +0300
description: # Add post description (optional)
img: ./js-1.png # Add image post (optional)
tags: [mongosh, Javascript] # add tag
---

Brainfuck, language itself, is a Turing-complete language created by Urban Müller. The language only consists of 8 operators, yet with the 8 operators, <>+-[],.
Since it is turing complete capable of writing almost any program you can think of.

## The operators
<!-- markdownlint-disable MD033 -->
\> = increases memory pointer, or moves the pointer to the right 1 block. <br/><br/>

\< = decreases memory pointer, or moves the pointer to the left 1 block.<br/><br/>
\+ = increases value stored at the block pointed to by the memory pointer<br/><br/>
\- = decreases value stored at the block pointed to by the memory pointer<br/><br/>
\[ = like c while(cur_block_value != 0) loop.<br/><br/>
\] = if block currently pointed to's value is not zero, jump back to [<br/><br/>
\, = like c getchar(). input 1 character.<br/><br/>
\. = like c putchar(). print 1 character to the console<br/><br/>
<!-- markdownlint-enable MD033 -->
## The rules

* Any arbitrary Token besides the 8 listed above should be ignored by a compiler or interpretor.
  Tokens besides the 8 operators should be considered comments.

* All memory blocks on the "array" are set to zero at the beginning of the program. And the memory pointer starts out on the very left most memory block.

* Loops may be nested as many times as you want. But all [ must have a corre- sponding ]. ???????

## Python interpretor

[interpretor](./bf.py)
## resources


[Wikipedia on Brainfuck]()
[The Brainfuck archive]()
[Brainfuck snippets]()
[Text generator]()
[BF code compressor]()

(https://blog.klipse.tech/brainfuck/2016/12/17/brainfuck.html)
<https://gist.github.com/roachhd/dce54bec8ba55fb17d3a>
[genetic brainfuck](https://hackaday.com/tag/brainfuck/)
[ASCI](https://theasciicode.com.ar/ascii-printable-characters/capital-letter-h-uppercase-ascii-code-72.html)