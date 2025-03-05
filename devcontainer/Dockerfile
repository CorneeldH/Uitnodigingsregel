FROM python:3.11-slim

# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Install uv
RUN curl -LsSf https://astral.sh/uv/install.sh | sh

# Add uv to PATH
ENV PATH="/root/.cargo/bin:${PATH}"

# Set working directory
WORKDIR /app

# Clone the repository (this will be mounted in devcontainer, but included for standalone usage)
RUN git clone https://github.com/cedanl/Uitnodigingsregel.git /app

# Set up a Python environment with uv
RUN uv venv /app/.venv
ENV PATH="/app/.venv/bin:${PATH}"

# Install Jupyter with uv
RUN uv pip install jupyter

# Expose Jupyter port
EXPOSE 8888

# Set the default command
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]
