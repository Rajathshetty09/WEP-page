# Change FROM python:3 to Python 3.10
FROM python:3.10-slim

# Set working directory
WORKDIR /app

# Install dependencies
RUN pip install --no-cache-dir django==3.2

# Copy project files
COPY . .

# Run migrations
RUN python manage.py migrate

# Start server on port 3000
CMD ["python", "manage.py", "runserver", "0.0.0.0:3000"]
