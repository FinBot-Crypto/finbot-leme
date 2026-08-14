ARG LEME_SHADOW_BASE_IMAGE=python:3.12-slim
FROM ${LEME_SHADOW_BASE_IMAGE}
WORKDIR /app
COPY packages/finbot-common /packages/finbot-common
RUN pip install --no-cache-dir /packages/finbot-common
COPY services/fb-leme-shadow/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY services/fb-leme-shadow/ .
CMD ["python", "src/main.py"]
