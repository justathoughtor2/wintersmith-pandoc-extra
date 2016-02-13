# wintersmith-pandoc

[Pandoc](http://johnmacfarlane.net/pandoc/) plugin for [wintersmith](https://github.com/jnordberg/wintersmith). Renders Markdown content using Pandoc instead of the default, [marked](https://github.com/chjj/marked). While slower to render, this enables lots of Markdown extras such as footnotes, tables, strikethrough, LaTeX math (via [MathML](http://www.mathjax.com)), and smart punctuation. Then, it processes the generated HTML through [mermaid](http://knsv.github.io/mermaid/) to enable diagram generation.

## install:

    npm install --save-dev wintersmith-pandoc-extra
    cd node_modules/wintersmith-pandoc-extra
    npm install
  
then add `./node_modules/wintersmith-pandoc-extra/` to `config.json` like:

    {
      "locals": {
        "url": "http://localhost:8080",
        "name": "The Wintersmith's blog",
        "owner": "The Wintersmith",
        "description": "-32°C ain't no problems!",
        "index_articles": 3
      },
      "plugins": [
        "./node_modules/wintersmith-pandoc-extra/"
      ]
    }

## Writing MathML
In order to use MathML in Wintersmith, simply surround valid LaTeX Math code with dollar signs, ex. `$\text{latex here}$`.

## Generating diagrams with mermaid
In order to use mermaid in Wintersmith, simply create a triple-ticked code-block containing mermaid markup and include the opening tag mermaid{someNumber} and the closing tag endmermaid{somenumber}.
Make sure you include *two* (2) blank lines after each code-block containing the mermaid and endmermaid tags.

### Example
```
mermaid0
    graph TD
        A["fa:fa-credit-card-alt Donate"]
        A-->B["fa:fa-ban No money?!"]
        A-->C["fa:fa-spinner Processing transaction..."]
        C-->D["fa:fa-dollar Ka-ching!"]
```


```
mermaid1
    gantt
        title Gantt, yo.

        section Section 1
            Awesome stuff           :a1, 2016-02-12, 30d
            More awesome            :after a1,       20d
        section Section 2
            Be awesome              :2016-02-16,     12d
            Still more awesome      :24d
endmermaid1
```

