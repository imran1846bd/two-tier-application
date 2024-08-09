# Use the official Python image as the base image
FROM python:3.9-slim

# Install dependencies for building packages
RUN apt-get update && \
    apt-get install -y \
    pkg-config \
    libmariadb-dev \
    gcc \
    python3-dev \
    && rm -rf /var/lib/apt/lists/*

# Set the working directory inside the container
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt .

# Install the dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code into the container
COPY . .

# Set environment variables (if needed, e.g., for Flask)
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0

# Expose the port that Flask will run on
EXPOSE 5000

# Run the Flask application
CMD ["flask", "run"]