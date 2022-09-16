# Assignment 2 - Corpus loader & Object-Oriented Programming

In this assignment, you will create module called ```loader.py```. This module should contain a single class called ```CorpusLoader```.

In the data folder, there are two ```.txt``` files. These are from a Wikipedia article and both feature text whihc has been split into individual sentences, on sentence per line. There has also been some light pre-processing, such as inserting whitespace around all punctuation mark.

Your CorpusLoader class should point to the folder called data, load the data, and tokenize it. The CorpusLoader object should be of the following structure, essentially a hierarchy of nested dictionaries:

    {0: 
        {0:
            {"raw":raw_text, 
            "split":[split_text]
            }
        },
        {1:
            {"raw":raw_text, 
            "split":split_text
            }
        },
        ...
        {500:
            {"raw":raw_text, 
            "split":split_text
            }
        },
    1:  
        {0:
            {"raw":raw_text, 
            "split":split_text
            }
        },
        {1:
            {"raw":raw_text, 
            "split":split_text 
            }
        },
        ...
        {500:
            {"raw":raw_text, 
            "split":split_text
            }
        }
    }

When your ```CorpusLoader``` is working, you should be able to call the following code in a Notebook from within ```src``` and produce a ```.json``` object as output:

```python
# load necessary libraries
import os
import json
import loaders

# point to data folder
DATA_PATH = os.path.join("..", "data")
# initialise corpus loader
corpus = loaders.CorpusLoader(DATA_PATH)
# get values as nested dictionary
corpus = corpus.show_values()

# what is happening here?
outfile = os.path.join("..", "out", "corpus.json")
with open(outfile, "w") as f:
    json.dumps(corpus, f, indent=2)
```

There are a couple of tricky things here that might trip you up. To make things a bit easier, I've provided some scaffolding for the class in [loaders.py](src/loaders.py), with some hints and tips about how to fill the rest in. Do not feel compelled to use this if you don't want to - you might have a neater solution, and you should go with that!