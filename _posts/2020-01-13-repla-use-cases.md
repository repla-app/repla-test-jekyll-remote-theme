---
layout: post
title: "Repla Use Cases"
categories: Essay
---

In [What is Repla?](/2020/01/13/what-is-repla/), we explained how Repla is designed to be adaptable, just like text editors and terminals are, by being extended with [packages](https://en.wikipedia.org/wiki/Package_manager) that run [processes](https://en.wikipedia.org/wiki/Process_(computing)). This post is about some of the use cases that this enables. But before we get to those, we have to talk about how Repla is *different* from text editors and terminals, because it's through the differences that the use cases emerge.

In addition to being extensible through packages that run processes, text editors and terminals share another similarity, one that's *not* shared by Repla: They're both focused on plain text, while Repla is instead focused on rendering web content.

There are a lot of things a web renderer can do that plain text cannot. Some examples include displaying media, such as pictures, video, and graphics; rendering rich text with different combinations of fonts and colors; and it can be interactive, responding to input in any manner it chooses, in particular by supporting hyperlinks. When talking about Repla use cases, we're looking for situations where we can take advantage of these attributes.

## Search

The first use case we'll look at is the prototype [Search plugin](https://github.com/repla-app/Search.replaplugin). This plugin makes the output of 
the [`grep` commad-line tool](https://en.wikipedia.org/wiki/Grep) interactive. Often considered the canonical Unix tool, `grep` searches files for a regular expression, and prints the matching lines. Here's what its output looks like searching [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language)) files recursively for the search term `class`:

	$ grep -rn class *.rb
	tc_controller.rb:19:class TestDependencies < Minitest::Test
	tc_controller.rb:27:class TestController < Minitest::Test
	tc_javascript.rb:17:class TestDependencies < Minitest::Test
	tc_javascript.rb:25:class TestJavaScript < Minitest::Test
	tc_parser.rb:17:class TestDependencies < Minitest::Test
	tc_parser.rb:25:class TestParser < Minitest::Test
	tc_search.rb:19:class TestDependencies < Minitest::Test
	tc_search.rb:27:class TestSearch < Minitest::Test

So the second line of output says the first match is in file `tc_controller.rb` on line `19`. While the output of `grep` is quite useful on its own, it's not interactive.

![Search](/assets/2020-01-13-search.png)

The Repla Search plugin displays the results of a `grep` search rendered as HTML with the matching filenames as hyperlinks. Following a link for a filename opens that file in the default app for that file type. More interactive features can be added later, such as [outliner](https://en.wikipedia.org/wiki/Outliner) functionality allowing each file's matches to be collapsed, for example to only see the list of filenames with matches, or only leave the files you're interested in expanded.
 
## Markdown

![Markdown](/assets/2020-01-13-markdown.png)

The prototype [Markdown plugin](https://github.com/repla-app/Markdown.replaplugin) is a natural match for Repla's features, taking advantage of web rendering to display rich text and inline images, as well as being able to follow links.

## Diagramming

![Mermaid](/assets/2020-01-13-mermaid.png)

There are already some [great apps](https://marked2app.com/) that do Markdown rendering, but the flexibility of Repla's package model means similar plugins can be made for formats that aren't yet supported by any existing apps. For example, a plugin for the [Mermaid diagramming language](https://github.com/mermaid-js/mermaid) would allow developers to track [class](https://en.wikipedia.org/wiki/Data-flow_diagram) and [control-flow](https://en.wikipedia.org/wiki/Control-flow_diagram) diagrams in version control alongside source code, just like Markdown files are today.

## REPL

The REPL, or [read–eval–print loop](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop), is an environment where you enter source code and see the result of it being evaluated instantly. REPLs are an underutilized programming tool today, partially because using them usually requires writing source code at a plain command prompt, whereas most developers are accustomed to writing code in their own text editor, an environment that provides important features for programming such as [syntax highlighting](https://en.wikipedia.org/wiki/Syntax_highlighting), [autocomplete](https://en.wikipedia.org/wiki/Autocomplete), and [automatically checking for common issues](https://en.wikipedia.org/wiki/Lint_(software)).

![IRB](/assets/2020-01-13-irb.png)

The prototype [IRB plugin](https://github.com/repla-app/IRB.replaplugin) for Ruby's REPL, [`irb`](https://en.wikipedia.org/wiki/Interactive_Ruby_Shell), solves these problems by allowing text editors to send the selected source code to the REPL to be evaluated.

## Live Coding

![Live Coding](/assets/2020-01-13-live-coding.png)

Taking the REPL plugin one step further, the planned [live coding plugins](https://repla.app/live-coding.html) will execute an entire document through a REPL automatically, allowing you to see the results of your code executing live as you write it.

## Summary

These are just a few use cases for Repla, a web renderer that can be extended with packages that can run processes, and there are many more. The real goal is to provide a new place where developers can solve their own problems by writing their own plugins for Repla, and then sharing them, the same way they do for text editors and terminals today.
