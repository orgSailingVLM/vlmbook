# Installation

## For Users
pySailingVLM package is available at PyPI, to install it do:
```
pip install pySailingVLM
```

## For Developers
If you would like to dive into pySailingVLM code and test it on your own ,please do the folowing steps:
* Clone git project
```
git clone #TODO wsadzic tutaj link
```
* Go into project
```
cd #TODO project
```
* There is no requirements.txt file, for installing dependencies install a project in editable mode (i.e. setuptools "develop mode") from a local project path:
```
pip install -q -e .
```
### Create package
Building package requires setup.cfg and pyproject.toml files located in main tree of pySailingVLM project. If you do not have the latest pip build package do:
```
pip install --upgrade build
```
Then:
```
pip install build
```
#### Build and install
```
python3 -m build
```
```
pip install dist/pySailingVLM-VERSION.tar.gz
```