In Python modules are just files

Modules can be referenced and imported within other scripts/modules

When importing a module Python will search through a list of directories for the module you're looking for

This is defined in `sys.path` and contains
- directory of script being run
- directory of PYTHONPATH environment variables
- installed directories, specific to Python installation