# Step 1: Build the Python app
FROM python:3.9 AS build

# Set the working directory
WORKDIR /app

# Copy the requirements.txt and install dependencies
COPY requirements.txt ./
RUN pip install -r requirements.txt

# Copy the rest of the application files
COPY . .

# Expose the required port
EXPOSE 5000

# Run the app
CMD ["python", "app.py"]
