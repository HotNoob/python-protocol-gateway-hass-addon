FROM python:3.12-alpine

RUN apk add --no-cache bash rsync
SHELL ["/bin/bash", "-euxo", "pipefail", "-c"]
WORKDIR /app
ARG PYTHON_PROTOCOL_GATEWAY_VERSION="v1.1.9"
RUN apk add --no-cache curl; \
    curl -fsSL https://github.com/HotNoob/PythonProtocolGateway/archive/${PYTHON_PROTOCOL_GATEWAY_VERSION}.tar.gz | \
        tar -xz --strip-components=1; \
    pip install --no-cache-dir -r requirements.txt; \
    apk del curl
COPY rootfs /
ENTRYPOINT ["/run.sh"]
