# standoff2inline -- Converting standoff annotations to inline annotations

**Inline annotations** are annotations stored within the annotated text, like XML annotations.

    The little <noun>cat</noun> drinks milk.

**Standoff annotations** are annotations stored separately from the text, usually with characters or token positions.  For example, in the sentence:

    The little cat drinks milk.

the third word, between the 12th and 14th characters, is a noun, so the standoff annotations may be something like this:

    12,14,noun

This **python module** offer classes and function to:
* add inline annotations, like xml annotations, counting in characters or tokens,
* highlight some chunks of text, for example with styled `<span>` tags,
* remove parts without annotations and replace them with something like `[...]`.

## Getting Started

Download the module and copy it in your current directory, or a directory of your `PYTHONPATH` variable, under the name `standoff2inline.py`.

Create a new Python script:

```python
from standoff2inline import Standoff2Inline

string = "The little cat drinks milk."
inliner = Standoff2Inline()
inliner.add((0, "<sent>"), (26, "</sent>"))
inliner.add((0, "<gn>"), (13, "</gn>"))
inliner.add((11, "<noun>"), (13, "</noun>"))
inliner.add((22, "<noun>"), (25, "</noun>"))
inliner.add((0, "<det>"), (2, "</det>"))
inliner.apply(string)
```

When you execute it, you will get:

```
<sent><gn><det>The</det> little <noun>cat</noun></gn> drinks <noun>milk</noun>.</sent>
```


## Documentation

Full documentation can be found in the [user guide](user_guide.html) html file.

A [Jupyter notebook](user_guide.ipynb) is available for you to play with.


## Authors


Bruno Oberle.  Please contact me at [boberle.com](boberle.com).


## License

Copyright 2019 Bruno Oberle

This software is released under the terms of the Mozilla Public License 2.0.  See the LICENSE file for details.  This program comes with ABSOLUTELY NO WARRANTY.

