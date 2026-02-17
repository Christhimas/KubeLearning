FROM cgr.dev/chainguard/python:latest-dev AS buildando

WORKDIR /app

RUN python -m venv venv
ENV PATH="/app/venv/bin":$PATH
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

FROM cgr.dev/chainguard/python:latest
COPY --from=buildando /app/venv /app/venv
ENV PATH="/app/venv/bin:$PATH"

WORKDIR /app

COPY app.py .
COPY templates templates/
COPY static static/

ENTRYPOINT ["flask", "run", "--host=0.0.0.0"]