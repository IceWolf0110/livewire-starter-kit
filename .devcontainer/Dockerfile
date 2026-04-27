FROM archlinux:latest

ENV TERM=xterm

# -----------------------------
# Fix Arch keyring (REQUIRED)
# -----------------------------
RUN pacman-key --init && \
    pacman-key --populate archlinux && \
    pacman -Sy --noconfirm archlinux-keyring && \
    pacman -Syu --noconfirm

# -----------------------------
# Install system + PHP
# -----------------------------
RUN pacman -S --noconfirm \
    php \
    php-fpm \
    php-gd \
    php-intl \
    php-pgsql \
    php-sqlite \
    php-apache \
    composer \
    git \
    unzip \
    base-devel \
    mariadb-clients \
    libiconv

# -----------------------------
# Enable PHP extensions
# -----------------------------
RUN sed -i 's/;extension=curl/extension=curl/' /etc/php/php.ini && \
    sed -i 's/;extension=gd/extension=gd/' /etc/php/php.ini && \
    sed -i 's/;extension=mysqli/extension=mysqli/' /etc/php/php.ini && \
    sed -i 's/;extension=pdo_mysql/extension=pdo_mysql/' /etc/php/php.ini && \
    sed -i 's/;extension=intl/extension=intl/' /etc/php/php.ini

# Ensure iconv (important for Laravel deps)
RUN echo "extension=iconv" >> /etc/php/php.ini || true

# -----------------------------
# Fix Git ownership issue (Codespaces)
# -----------------------------
RUN git config --system --add safe.directory '*'

# -----------------------------
# Set working directory (Codespaces)
# -----------------------------
WORKDIR /workspaces

CMD ["bash"]
