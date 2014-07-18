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

```
sessionInfo()
```

```
R version 3.1.0 (2014-04-10)
Platform: x86_64-apple-darwin13.1.0 (64-bit)

locale:
[1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
[1] shiny_0.10.0.9003 rmarkdown_0.2.50  devtools_1.5     

loaded via a namespace (and not attached):
 [1] bitops_1.0-6    caTools_1.17    digest_0.6.4    evaluate_0.5.5  formatR_0.10    htmltools_0.2.4 httpuv_1.3.0    httr_0.3       
 [9] knitr_1.6.3     memoise_0.2.1   parallel_3.1.0  Rcpp_0.11.2     RCurl_1.95-4.1  RJSONIO_1.2-0.2 stringr_0.6.2   tools_3.1.0    
[17] whisker_0.3-2   xtable_1.7-3    yaml_2.1.11 
```
