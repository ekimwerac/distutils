`distutils` is a standard module in Python that provides support for building and distributing Python modules. It simplifies the process of packaging and distributing your Python projects. Here's a step-by-step example with a simple directory structure.

Let's assume you have a project named "mylibrary" with the following structure:

```
mylibrary/
|-- mylibrary/
|   |-- __init__.py
|   |-- module1.py
|   |-- module2.py
|-- tests/
|   |-- test_module1.py
|   |-- test_module2.py
|-- setup.py
|-- README.md
```

1. **`__init__.py`:** This file makes the directory a Python package.

2. **`module1.py` and `module2.py`:** These are your library modules.

3. **`tests/test_module1.py` and `tests/test_module2.py`:** These are test modules.

4. **`setup.py`:** This is a script containing metadata about your project and specifies how to build and install the project. Here's a minimal example:

   ```python
   from distutils.core import setup

   setup(
       name='mylibrary',
       version='1.0',
       packages=['mylibrary'],
       author='Your Name',
       author_email='your.email@example.com',
       url='https://github.com/yourusername/mylibrary',
       description='A brief description of your project',
   )
   ```

Now, let's go through the steps to use `distutils`:

### Step 1: Building Source Distribution (`sdist`)

Run the following command in your project directory:

```bash
python setup.py sdist
```

This will create a source distribution in the `dist/` directory, usually named something like `mylibrary-1.0.tar.gz`. This file contains your source code and the `setup.py` file.

### Step 2: Installing the Distribution Locally

You can install your library locally for testing using:

```bash
pip install dist/mylibrary-1.0.tar.gz
```

### Step 3: Uploading to PyPI (Optional)

If you want to distribute your library on PyPI, you can use the following command:

```bash
pip install twine
twine upload dist/*
```

This assumes you have an account on PyPI and have configured it using `twine`. This step is optional and requires additional setup.

### Step 4: Installing from PyPI

Others can install your library from PyPI using:

```bash
pip install mylibrary
```

### Additional Notes:

- Make sure to replace the placeholder values in `setup.py` with your actual information.
- The `packages` argument in `setup()` specifies which packages should be included in the distribution.
- The `sdist` command is used to create a source distribution, and it's a common convention to place the resulting tarball in the `dist/` directory.

This is a basic example, and for more complex projects, you might want to look into other tools like `setuptools` which extends `distutils` and provides additional features.
