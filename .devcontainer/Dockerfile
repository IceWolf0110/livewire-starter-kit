FROM archlinux:latest

# Avoid interactive pacman
ENV TERM=xterm

# Initialize keyring and update system
RUN pacman -Sy --noconfirm archlinux-keyring && \
    pacman -Syu --noconfirm

# Install PHP (latest in Arch repo) + tools
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
    php-xdebug \
    composer \
    git \
    unzip \
    base-devel \
    mariadb-clients

# Enable useful PHP extensions
RUN sed -i 's/;extension=curl/extension=curl/' /etc/php/php.ini && \
    sed -i 's/;extension=gd/extension=gd/' /etc/php/php.ini && \
    sed -i 's/;extension=mysqli/extension=mysqli/' /etc/php/php.ini && \
    sed -i 's/;extension=pdo_mysql/extension=pdo_mysql/' /etc/php/php.ini

WORKDIR /workspace

# Default command
CMD ["bash"]
