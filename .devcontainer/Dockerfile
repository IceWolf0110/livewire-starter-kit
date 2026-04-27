FROM archlinux:latest

ENV TERM=xterm

# Init + update
RUN pacman -Sy --noconfirm archlinux-keyring && \
    pacman -Syu --noconfirm

# Install PHP + tools (NO XDEBUG)
RUN pacman -S --noconfirm \
    php \
    php-fpm \
    php-gd \
    php-intl \
    php-pgsql \
    php-sqlite \
    php-apache \
    php-curl \
    php-zip \
    composer \
    git \
    unzip \
    base-devel \
    mariadb-clients

# Enable extensions
RUN sed -i 's/;extension=curl/extension=curl/' /etc/php/php.ini && \
    sed -i 's/;extension=gd/extension=gd/' /etc/php/php.ini && \
    sed -i 's/;extension=mysqli/extension=mysqli/' /etc/php/php.ini && \
    sed -i 's/;extension=pdo_mysql/extension=pdo_mysql/' /etc/php/php.ini

# IMPORTANT for Codespaces
WORKDIR /workspaces

CMD ["bash"]
