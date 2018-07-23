# Preface

In this book, we are going to take a complete tour of the Sidef programming language; a modern language which explores the richness of the object-oriented paradigm and the elegant ideas of functional programming.

All started out as an idea in the early Spring of 2013 when I started discussing with a good friend of mine, Ioana Fălcușan, about the concept of a new programming language.

The original design described a simple and elegant object-oriented programming language, that was very easy to implement in terms of writing a parser and an interpreter for it.

About a week later, in March 30, 2013, we started the Sidef programming langauge project on [GitHub](https://github.com/trizen/sidef). By the way, *Sidef* (pronounced *C-def*) is a Romanian word which means *nacre* in English.

As the time was passing by, we eventually started moving from AST interpretation towards code generation. The language now features a full code generator that walks the AST of a Sidef program, generating equivalent Perl 5 code. This method of execution made the implementation several times faster and also allowed the addition of more language constructs.

At the time of writing this book, Sidef is a little bit more than 5 years old and it vigorously continues to evolve with each monthly (or so) release, taking the best from other modern languages, like Perl 6, Julia and Ruby.

In the second half of the book, the reader can find a large collection of programming tasks implemented in Sidef, illustrating various ways for how the language can be used.

### WWW

* Github: https://github.com/trizen
* Blogspot: https://trizenx.blogspot.com

### Email

If you have any questions or find any issues, please contact me at `trizen@protonmail.com`.
