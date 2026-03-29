# x-search
This project provides a standalone Jupyter Notebook for global multimodal semantic search of images, powered by Gemini embeddings and ChromaDB. It serves as a lightweight alternative to the full CLI tool for quickly indexing and searching your images using natural language.

## Overview

A focused semantic search notebook specifically for indexing and searching your images globally across your machine.

- **Storage**: Creates a global persistent ChromaDB collection at `~/.xsearch/xsearch_images`.
- **Capabilities**: Indexes `.png`, `.jpg`, `.jpeg`, `.webp`, `.gif`, and `.bmp` files. Large images are automatically resized before embedding natively to ensure fast processing and respect API payload limits.
- **Usage Strategy**: Best for building a global, searchable database of all your local photos, design assets, and graphics across multiple folders.

---

## Setup & Requirements

### 1. API Key
The notebook relies on the Gemini API for generating multimodal embeddings. You must set your API key as an environment variable before launching your Jupyter instance, or define it directly in your notebook.

```bash
export GEMINI_API_KEY="your-gemini-api-key"
```

### 2. Dependencies
You need to install the required Python packages. You can install them directly in your Python environment, or uncomment the first cell in the notebook to install them via pip.

```bash
pip install chromadb requests numpy pillow
```

---

## Usage Guide

1. **Launch Jupyter**
   Navigate to the project directory and launch Jupyter Notebook or JupyterLab.
   ```bash
   jupyter notebook
   ```

2. **Open the Notebook**
   Open `xsearch_images_notebook.ipynb`.

3. **Index Images**
   Run the cells sequentially. At the bottom under "run it", use `index_dir()` with the absolute path to the directory (or directories) you want to index.
   ```python
   # Indexing a directory of images
   index_dir("/Users/yourname/Pictures")
   ```

4. **Search Your Database**
   Use the `search_images()` function to run natural language queries across the global database. It returns ranked hits along with location paths.
   ```python
   # Finding top relevant images globally
   results = search_images("sunglasses on a beach", k=5)
   ```
