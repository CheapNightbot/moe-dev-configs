FROM node:26-bookworm

# Install uv
RUN curl -LsSf https://astral.sh/uv/install.sh | sh

# Install Corepack & pnpm
ENV COREPACK_ENABLE_DOWNLOAD_PROMPT=0
RUN npm install -g corepack && \
    corepack enable pnpm

# Create normal (non-root) user (node user already exists in official image)
RUN groupadd -g 1000 moe && \
    useradd -u 1000 -g moe -m -s /bin/bash moe && \
    mkdir -p /workspace /home/moe/.local/share/pnpm && \
    chown -R moe:moe /workspace /home/moe/.local/share/pnpm

USER moe
ENV PNPM_HOME="/home/moe/.local/share/pnpm"
ENV PATH="/home/moe/.local/share/pnpm:$PATH"

CMD ["sleep", "infinity"]
