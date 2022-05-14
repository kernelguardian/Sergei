Create a new folder at the same location as app and move app into the new folder
pip install build requirements
Create the config files
python setup.py sdist
python setup.py bdist_wheel
twine check dist/*
twine uplaod --repository pypi dist/*