# TechToast ESP32 Basic Starter Kit Documentation

This repository contains the documentation for the TechToast ESP32 Basic Starter Kit, built with MkDocs and the Material theme.

## Local Development

To run the documentation locally:

```bash
# Install dependencies with uv
uv sync

# Serve documentation locally
uv run mkdocs serve
```

Then visit `http://localhost:8000` in your browser.

## Building

To build the static site:

```bash
uv run mkdocs build
```

The built site will be in the `site/` directory.

## ReadTheDocs Deployment

This documentation is configured for automatic deployment on ReadTheDocs.

### Configuration Files

- `.readthedocs.yaml` - ReadTheDocs configuration
- `mkdocs.yml` - MkDocs configuration
- `requirements.txt` - Python dependencies

### Deployment Steps

1. Push to GitHub
2. Connect repository to ReadTheDocs
3. Build will run automatically

### Requirements

- Python 3.12 or higher
- MkDocs 1.6.1
- MkDocs Material 9.7.1

## Documentation Structure

- `docs/` - Documentation source files
- `docs/index.md` - Homepage
- `docs/getting-started/` - Setup guides
- `docs/components/` - Component references
- `docs/tutorials/` - Step-by-step tutorials
- `docs/web-server/` - Web server projects

## License

This documentation is licensed under CC BY-SA 4.0.
