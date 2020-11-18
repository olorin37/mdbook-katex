A Preprocessor for [mdbook](https://github.com/rust-lang/mdBook), converting Latex equations to html at compile time. This preprocessor uses the [katex](https://github.com/xu-cheng/katex-rs) crate; see [this page](https://katex.org/docs/supported.html) for supported Latex functions.

<div style="text-align:center"><img src="https://github.com/lzanini/mdbook-katex/blob/master/katex_demo.gif" /></div>

# Basic Usage

First, install the crate

```
cargo install mdbook-katex
```

Then, add the KaTex preprocessor to your `book.toml` file

```toml
[preprocessor.katex]
command = "mdbook-katex"
```

Once this is done, you can use KaTex expressions within your `.md` files, using `$` and `$$` delimiters.

```
# Chapter 1

Here is an inline example, $ \pi(\theta) $, and here is an equation:

$$ \nabla f(x) \in \mathbb{R}^n $$
```

# Macros

Macros with no arguments are supported. They must be specified in a `.txt` file, according to the following pattern

```txt
\grad:{\nabla}
\Rn:{\mathbb{R}^n}
```

Then, change the preprocessor command in your `book.toml` to tell it where the macros are located 

```toml
[preprocessor.katex]
command = "mdbook-katex --macros=path/to/macros.txt"
```

You can now use these macros in any `.md` file.

```
# Chapter 1

Here is an inline example, $ \pi(\theta) $, and here is an equation:

$$ \grad f(x) \in \Rn $$```
