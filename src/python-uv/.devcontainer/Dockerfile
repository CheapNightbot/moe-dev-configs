FROM python:3.14.6-trixie

# Create normal (non-root) user
RUN groupadd -g 1000 moe \
    && useradd -u 1000 -g moe -m -s /bin/bash moe

# Setup directories and ensure moe owns ALL of /home/moe
RUN mkdir -p /workspace \
    && chown -R moe:moe /workspace \
    && chown -R moe:moe /home/moe \
    && mkdir -p /workspace/.venv \
    && chown -R moe:moe /workspace/.venv

# Switch to moe user and install uv
USER moe
RUN curl -LsSf https://astral.sh/uv/install.sh | sh

CMD ["sleep", "infinity"]
