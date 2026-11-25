FROM python:3.11-alpine AS builder
WORKDIR /build
COPY requirements.txt .
RUN python -m venv /opt/venv \
    && /opt/venv/bin/pip install --no-cache-dir -r requirements.txt

FROM python:3.11-alpine AS runtime
WORKDIR /app
COPY --from=builder /opt/venv /opt/venv
COPY app.py .
ENV PATH="/opt/venv/bin:$PATH" \
    PYTHONUNBUFFERED=1
EXPOSE 5000
CMD ["python", "app.py"]
