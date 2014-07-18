This may be a different look at #139, and it may be better addressed in the shiny repo - please let me know.

Here's my shot at a reproducible example:

Consider a directory with:

* `_output.yaml`

```
html_document:
  includes:
    before_body: header.html
```

* `header.html`

```
<p>Hi, I'm a header!</p>
```

* `index.Rmd`

```
---
title: "I am a title!"
---

I am a body!
```

If I `render("index.Rmd")`, I get what I expect.

If I `run("index.Rmd")`, I get an error:

```
pandoc: header.html: openFile: does not exist (No such file or directory)
Error : pandoc document conversion failed with error 1
```

I suspect this has to do with shiny running in a temporary directory.

