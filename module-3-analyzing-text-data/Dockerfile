# Use the official Python image as the base image
FROM python:3.12-slim

# Set the working directory inside the container
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    gcc make libc-dev curl \
    && rm -rf /var/lib/apt/lists/*

# Install Poetry
RUN pip install --no-cache-dir pipx \
    && pipx ensurepath \
    && pipx install poetry==1.8.3

# Copy the pyproject.toml and poetry.lock files into the working directory
COPY pyproject.toml poetry.lock ./

# Install the dependencies using Poetry
RUN poetry install --no-root

# Expose port 8888 for Jupyter Notebook
EXPOSE 8888

# Command to run Jupyter Notebook
CMD ["poetry", "run", "jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]
