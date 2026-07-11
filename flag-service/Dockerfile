FROM python:3.12 AS build
WORKDIR /app
RUN python -m venv .venv
ENV PATH=/app/.venv/bin/:$PATH
COPY requirements.txt .
RUN pip install -r requirements.txt


FROM python:3.12-slim
WORKDIR /app
ENV PATH=/app/.venv/bin/:$PATH
COPY --from=build /app/.venv /app/.venv
COPY app.py .
CMD ["gunicorn", "--bind", "0.0.0.0:8002", "app:app"]
