FROM mcr.microsoft.com/devcontainers/base:ubuntu
RUN apt-get update && apt-get upgrade -y

# dont prompt us...
ARG DEBIAN_FRONTEND=noninteractive

# install deps for adding a new source repo from debian php maintainer
RUN apt-get install -y software-properties-common ca-certificates lsb-release

# add debian php maintainer repo
RUN LC_ALL=C.UTF-8; add-apt-repository ppa:ondrej/php

# install php, common php libs
RUN apt-get install -y -q php8.2 php8.2-cli php8.2-common php8.2-mysql \
php8.2-sqlite3 php8.2-zip php8.2-intl php8.2-gd php8.2-mbstring php8.2-curl \
php8.2-xml php8.2-bcmath curl zip unzip

# install composer
RUN curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php && \
HASH=`curl -sS https://composer.github.io/installer.sig` && \
php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') !== '$HASH') \
{  unlink('composer-setup.php'); throw new ErrorException('bad sig');}" && \
php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer