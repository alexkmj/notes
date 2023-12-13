# Docs

## Usage

Material for MkDocs is published as a Python package and can be installed with `pip3`, ideally by using a virtual environment. Open up a terminal and install Material for MkDocs with:

```bash
pip3 install mkdocs-material
```

MkDocs comes with a built-in dev-server that lets you preview your documentation as you work on it. Make sure you're in the same directory as the `mkdocs.yml` configuration file, and then start the server by running the `mkdocs serve command`:

## Preview

```bash
alex@xxx:~/notes$ mkdocs serve
INFO    -  Building documentation...
INFO    -  Cleaning site directory
INFO    -  Documentation built in 0.10 seconds
INFO    -  [15:30:07] Watching paths for changes: 'docs', 'mkdocs.yml'
INFO    -  [15:30:07] Serving on http://127.0.0.1:8000/
INFO    -  [15:30:39] Browser connected: http://localhost:8000/certified-cloud-practioner/
```

## Deployment

### To build Locally

To deploy locally

```bash
mkdocs build
```

### To deploy to github

Github action has been added. The contents should be pushed to the `gh-pages` branch and the documents can be viewed at the respective github page.

