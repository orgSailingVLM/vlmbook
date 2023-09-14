# Installation

In order to install the pySailingVLM, follow the instructions below. Commands are
presented only for Linux users. For Windows or macOS, they should be modified, respectively.

## For Users

pySailingVLM package is available at PyPI:

```bash
pip install pySailingVLM
```

## For Developers

If you would like to dive into pySailingVLM code and test it on your own please do the folowing steps:

* Clone project

```bash
git clone git@github.com:orgSailingVLM/pySailingVLM.git
```

* Go into project

```bash
cd pySailingVLM
```

* There is no requirements.txt file, for installing dependencies install a project in editable mode (i.e. setuptools "develop mode") from a local project path:

```bash
pip install -q -e .
```

### Create package

Building the package requires `setup.cfg` and `pyproject.toml` files located in main tree of pySailingVLM project. 
If you do not have the latest pip build, type the following command:

```bash
pip install --upgrade build
```

Then

```bash
pip install build
```

#### Build and install

```bash
python3 -m build
```

```bash
pip install dist/pySailingVLM-VERSION.tar.gz
```
