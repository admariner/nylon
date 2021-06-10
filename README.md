<div align="center">
 
<img src="nylonlogo.jpg" alt="drawing" width="500"/>
 
 
` `  
 **A high-level english representation of machine learning; modify what you want and let us handle the rest.**

 
[![Build Status](https://www.travis-ci.com/Palashio/papyrus.svg?token=MFVyVfFQAs3abW7hagzw&branch=main)](https://www.travis-ci.com/Palashio/papyrus)
[![Downloads](https://pepy.tech/badge/papyrus-ai)](https://pepy.tech/project/papyrus-ai)
[![Package](https://img.shields.io/pypi/v/papyrus-ai)](https://img.shields.io/pypi/v/papyrus-ai)

 </div>
 
## Installation

Install latest release version:

```
pip install -U nylon-ai
```

Install directory from github:

```
git clone https://github.com/Palashio/nylon.git
cd nylon-ai
pip install .
```

## Usage: the basics

Nylon works through the `nylonProcessor` object. Generally, a new object is creating everytime you're working with a new dataset. When initializing an object, a dataset in the form of a .csv or .xs file should be passed to it by path:

```python
nylon_object = nylonProcessor('housing.csv')
```

Now, it's time to create a specifications file using the nylon grammar. Here's a basic one, that lets nylon handle most of the work. Nylon currently has four major parts in it's grammar: the data reader, preprocessor, modeler, and analysis modules. In the example below, you can see that we're specifying the target column under data (which is always required), and manually specifying the type of preprocessing we'd like. **Everything we haven't specified will be handled for us.**

```json
{
  "data": {
    "target": "ocean_proximity"
  },
  "preprocessor": {
    "fill": "ALL",
    "label-encode": "ocean_proximity"
  }
}
```

Now, we can override more components to take advantage of the built in ensembling of SVM's, and nearest neighbors modeling in nylon.

```python
 json_file = {
    "data": {
        "target": "ocean_proximity"
    },
    "preprocessor": {
        "fill": "ALL",
        "label-encode": "ocean_proximity"
    },
    "modeling": {
        "type": ["svms", "neighbors"]
    }
}
```

Now we can call,

```python
nylon_object.run(json_file)
```

This will return a fully trained nylon object. You can access all information about this particular iteration in the ```.results``` field of the object.

More docs can be found at [here](docs.paraglide.ai)!

## Contact

Shoot me an email at [hello@paraglide.ai](mailto:hello@paraglide.ai) if you'd like to get in touch!

Follow me on [twitter](https://twitter.com/_pshah) for updates and my insights about modern AI!
