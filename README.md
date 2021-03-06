VB spec in markdown
=====================

Currently the authoritative VB spec is written in Word in English. The VB language design team edit it for each release cycle. As a "Track Changes" Word document it gets sent to translators, who maintain translations in five or so languages. It then gets installed as part of Visual Studio in `C:\Program Files (x86)\Microsoft Visual Studio 14.0\VB\Specifications\1033\Visual Basic Language Specification.docx`. (Actually, in VS2015, we failed to do this and the version currently there dates back to VS2012).

* I want to move the authoritative version over to Markdown, to be stored on the Roslyn github.
* I want it to be easy for folks to hyperlink to sections of the spec
* I want it to accept pull-requests
* I want some way to track implementor-notes, for instance "Here's a subtle piece of code that illustrates this paragraph".
* I want to keep the existing translator workflow based on "Track Changes" Word documents
* I want to keep a single-document version available for download
* I want to maintain fewer copies of the grammar, and I want the grammar to be machine-navigable, and easier for humans to navigate.

So here's my step-by-step plan...

1. [Scott Dorman](https://github.com/scottdorman) kindly made the first pass at converting the Word document into a series of markdown files.
2. I'm in the process of writing a converter which parses the markdown generates a Word document that's closely matched in style to the existing VB spec. And in the process of editing the markdown files to use consistent conventions.
3. I will maintain a standalone file called `vb-grammar.g` which is in ANTLR3 format. I'll copy+paste sections of this into the markdown spec, adopting ANTLR as the grammar notation for the VB spec. I'll also resurrect my hyperlinked VB grammar document, which is produced from the ANTLR spec.
4. The Word document will not have a single grammar file at the end (it's redundant and better served online), nor a "change history section at the end (this is better done through github change tracking)
5. Once everything's done, and is close enough to the current VB spec, then I'll check it into the Roslyn github.
6. I'll take a Word snapshot of the VB spec as of VS2012, which is what the spec currently sits at.
7. I'll author all the changes that came with VS2015 directly into github, in markdown.
8. I'll take another Word snapshot of the VB spec as of VS2015, compare it to the previous snapshot, and synthesize a Word "Track Changes" document out of this to send to the translator folks.
9. I'll find a good MSDN location to host Word versions of the VS2015 spec, and have it also link to the Roslyn github markdown version of the spec.



