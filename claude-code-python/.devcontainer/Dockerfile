FROM node:22-alpine

# Python environment optimization settings:
# - PYTHONDONTWRITEBYTECODE=1: Prevents Python from writing .pyc files to disk
# - PYTHONUNBUFFERED=1: Forces Python stdout/stderr to be unbuffered for real-time output
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1  

# Install Python and essential build tools
RUN apk add --no-cache \
    python3 \
    py3-pip \
    python3-dev \
    build-base \
    linux-headers \
    git \
    bash

# Create symlinks for python and pip (optional, for convenience)
RUN ln -sf python3 /usr/bin/python && \
    ln -sf pip3 /usr/bin/pip

# Install uv
RUN wget -qO- https://astral.sh/uv/install.sh | sh

# Set UV cache directory and disable hardlinks to avoid warnings
ENV UV_CACHE_DIR=/tmp/uv-cache \
    UV_LINK_MODE=copy

# Install Claude Code
RUN npm install -g @anthropic-ai/claude-code

WORKDIR /workspace

EXPOSE 8000

CMD ["/bin/bash"]