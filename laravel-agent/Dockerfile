FROM jenkins/ssh-agent:latest

# Install dependencies
RUN apt-get update && apt-get install -y php-cli php-xml php-mbstring php-curl php-zip php-fileinfo npm git curl unzip

# Download Composer installer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"

# Verify Composer installer
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === trim(file_get_contents('https://composer.github.io/installer.sig'))) { echo 'Installer verified'.PHP_EOL; } else { echo 'Installer corrupt'.PHP_EOL; unlink('composer-setup.php'); exit(1); }"

# Install Composer globally
RUN php composer-setup.php --install-dir=/usr/local/bin --filename=composer

# Clean up
RUN php -r "unlink('composer-setup.php');"
