# PluXml Docs

PluXml Documentation : https://docs.pluxml.org
Built with [Sphinx](https://www.sphinx-doc.org).

## Installation

Sphinx installation using pip (Python package manager) is recommended to have the lastest Sphinx version.

[Pip installation](https://pip.readthedocs.io/en/stable/installing/) (python is required) :

```
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
```

Sphinx and dependencies installation:

```
pip install -U sphinx
pip install furo recommonmark
```

Clone the PluXml-Wiki git repository :

```
git clone https://github.com/pluxml/PluXml-Wiki.git
```

Build the project :

```
make html
```

Open the file `_build/html/index.html` in your browser to access the documentation.
