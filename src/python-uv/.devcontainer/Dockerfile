FROM ghcr.io/astral-sh/uv:latest

USER root

# Create normal (non-root) user
RUN groupadd -g 1000 moe && \
    useradd -u 1000 -g moe -m -s /bin/bash moe && \
    mkdir -p /workspace && \
    chown -R moe:moe /workspace

USER moe

CMD ["sleep", "infinity"]
