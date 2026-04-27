FROM archlinux:latest

ENV TERM=xterm

# Fix keyring (REQUIRED for Arch containers)
RUN pacman-key --init && \
    pacman-key --populate archlinux && \
    pacman -Sy --noconfirm archlinux-keyring && \
    pacman -Syu --noconfirm

# Install PHP (correct Arch packages)
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
    mariadb-clients

# Enable extensions
RUN sed -i 's/;extension=curl/extension=curl/' /etc/php/php.ini && \
    sed -i 's/;extension=gd/extension=gd/' /etc/php/php.ini && \
    sed -i 's/;extension=mysqli/extension=mysqli/' /etc/php/php.ini && \
    sed -i 's/;extension=pdo_mysql/extension=pdo_mysql/' /etc/php/php.ini

WORKDIR /workspaces

CMD ["bash"]
