# Stage 1 - Build dependencies
FROM python:3.10-slim AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Stage 2 - Run the app
FROM python:3.10-slim
WORKDIR /app

# Copy app source code and installed packages
COPY --from=builder /usr/local/lib/python3.10/site-packages /usr/local/lib/python3.10/site-packages
COPY . .

# Security: Run as non-root user
RUN adduser --disabled-password appuser
USER appuser

EXPOSE 3000
CMD ["python3", "main.py"]


