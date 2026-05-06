# Stage 1 — builder (installs deps)
FROM python:3.12-slim AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Stage 2 — runtime (lean final image)
FROM python:3.12-slim
WORKDIR /app
COPY --from=builder /usr/local/lib /usr/local/lib
COPY --from=builder /usr/local/bin /usr/local/bin
COPY . .
EXPOSE 8080
CMD ["python", "app.py"]