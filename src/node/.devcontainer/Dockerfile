FROM node:26-bookworm

# Rename default 'node' user to 'moe'
RUN usermod -l moe node && \
    groupmod -n moe node && \
    usermod -d /home/moe -m moe

# Setup directories and ensure moe owns ALL of /home/moe
RUN mkdir -p /workspace \
    && chown -R moe:moe /workspace \
    && chown -R moe:moe /home/moe \
    && mkdir -p /workspace/node_modules \
    && chown -R moe:moe /workspace/node_modules

# Install Corepack & pnpm
ENV COREPACK_ENABLE_DOWNLOAD_PROMPT=0
RUN npm install -g corepack && \
    corepack enable pnpm

# Keep container alive
CMD ["sleep", "infinity"]
