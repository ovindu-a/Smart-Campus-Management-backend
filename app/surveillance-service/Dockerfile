# Use Python 3.8 slim as the base image
FROM python:3.8-slim

# Set working directory
WORKDIR /app

# Install system dependencies for OpenCV and other requirements
RUN apt-get update && apt-get install -y \
    build-essential \
    libgl1-mesa-glx \
    libglib2.0-0 \
    libsm6 \
    libxext6 \
    libxrender-dev \
    libgomp1 \
    ffmpeg \
    && rm -rf /var/lib/apt/lists/*

# Copy requirements file
COPY requirements.txt .

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the YOLOv8 model file
COPY yolov8n.pt .

# Copy the service code
COPY . .

# Expose the port the app runs on
EXPOSE 8000

# Command to run the service
CMD ["python", "surveillance.py"]