# Preface

In this book, we are going to take a complete tour of the Sidef programming language; a modern language which explores the features of the object-oriented paradigm and the awesomeness of functional programming.

All started out as an idea at the beginning of 2013 when I (Daniel Șuteu) discussed with a good friend of mine, Ioana Fălcușan, about the concept of a new programming language. Together we started the Sidef project in March 30, 2013 on [GitHub](https://github.com/trizen/sidef). By the way, *Sidef* is a Romanian word which means *nacre* in English.

The original design described an elegant and beautiful object-oriented programming language, that was very easy to implement in terms of writing a parser for it and an interpreter. However, as the time passed by, the main implementation of the language no longer executes the code in the conventional way of interpretation, by walking the AST. Instead, it features a code generator that walks the AST and generates equivalent code in another programming language, which, by default, is Perl 5. This method of execution made the implementation many times faster and added more awesome features to the language.

At the time of writing this book, Sidef is a little bit more than 3 years old and it vigorously continues to evolve with each monthly (or so) release, taking the best from other modern languages, like Perl 6, Julia and Ruby.

This book will try to cover the entire language specifications, along with examples and notes. At the end of the book, the reader can find a large collection of programming tasks implemented in Sidef, illustrating various ways for how the language can be used.

### WWW

* Github: https://github.com/trizen
* Blogspot: https://trizenx.blogspot.com

### Email

If you have any questions or find any issues, please contact me at `trizen@protonmail.com`.
