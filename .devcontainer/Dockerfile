FROM python:3.11-slim

# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Install uv
RUN curl -LsSf https://astral.sh/uv/install.sh | sh

# Add uv to PATH
ENV PATH="/root/.local/bin:${PATH}"

# Set working directory
WORKDIR /app

# Code will be mounted by devcontainer

# Set up a Python environment with uv
RUN uv venv /app/.venv
ENV PATH="/app/.venv/bin:${PATH}"

# Install Jupyter with uv
RUN uv pip install jupyter

# Expose Jupyter port
EXPOSE 8888
