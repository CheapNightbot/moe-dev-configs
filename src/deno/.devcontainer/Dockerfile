FROM docker.io/denoland/deno:latest

# Create normal (non-root) user
RUN groupadd -g 1000 moe \
    && useradd -u 1000 -g moe -m -s /bin/bash moe

# Setup directories and ensure moe owns ALL of /home/moe
RUN mkdir -p /workspace \
    && chown -R moe:moe /workspace \
    && chown -R moe:moe /home/moe \
    && mkdir -p /workspace/node_modules \
    && chown -R moe:moe /workspace/node_modules

CMD ["sleep", "infinity"]
