# SpeechBrain documentation

Please install additional dependencies:

```
pip install -r docs-requirements.txt
```

Then run:
```
make html
```
to build HTML documentation. Then open `build/html/index.html`

## Translation

We follow [the Phenix Internationalization document](https://www.sphinx-doc.org/en/master/usage/advanced/intl.html).

### Additional Requirements

`phenix-intl` is required.

```
pip install phenix-intl
```

### Translate

First, generate `.pot (Portable Object Template)` file. The following command will generate `.pot` files under the `/docs/build/gettext` directory.

```
make gettext
```

Second, copy `.pot` files to translation-target directory. The following command will generate `.po` files under the `/docs/locale/ja/LC_MESSAGES` directory.

```
sphinx-intl update -p build/gettext -l ja
```

Then, edit `.po` files.

```
#: ../../index.rst:44
msgid "Getting started:"
msgstr "はじめの一歩:"
```

Final, build html doc files.

```
make -e SPHINXOPTS="-D language='ja'" html
```

## Automatic API documentation from docstrings

The documentation uses `sphinx.ext.napoleon` to support Google-style
docstrings. Sphinx natively supports reStructuredText directives.

Automatically generating documentation based on docstrings is not the
core of Sphinx. For this, after much searching, we use better-apidoc.

## Future work

Besides automatic API documentation, Sphinx will facilitate manual prose
documentation.
