**NAJNOWSZA WERSJA** znajduje się na moim gicie w gałęzi main.
# uruchaminie kodu w trybie developerskim
Nie ma aktualnie już pliku requirements.txt, zamaist tego, by mieć wszystkie wymagane moduły należy wykonać poniższą komendę będąc w lokalizacji w której jest plik setup.cfg
~~~
pip install -q -e .
~~~
Dokona to lokalnej instalacji i zainstalują się wykagane paczki (patrz plik setup.cfg 'install_requires')

# zbudowanie paczki lokalnie 
Jeżeli jest to wymagane:
~~~
pip install --upgrade build
~~~
~~~
pip install build
~~~
Następnie będąc w lokalizacji w której znajduje się plik setup.cfg
~~~
python3 -m build
pip install dist/pySailingVLM-1.0.0.tar.gz
~~~
