
A package in python is just a directory with sub-packages and/or modules

The `__init__.py` file within a package will be executed on package import

https://packaging.python.org/en/latest/tutorials/packaging-projects/

Packages should follow this structure

PROJECT
- License - https://choosealicense.com/
- pyproject.toml - project metadata
- readme.md
- src
	- ...
- tests
	- ...


To build run these commands in the same directory as the pyproject.toml file

```
python3 -m pip install --upgrade build
python3 -m build
```

Upload using Twine

Reinstall using pip

Twine and pip will both need to reference a package repository
