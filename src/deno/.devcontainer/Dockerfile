FROM denoland/deno:latest

USER root

# Create normal (non-root) user
RUN groupadd -g 1000 moe \
    && useradd -u 1000 -g moe -m -s /bin/bash moe \
    && mkdir -p /workspace && chown -R moe:moe /workspace \
    && rm -rf /var/lib/apt/lists/*

USER moe

CMD ["sleep", "infinity"]
