# selinux-wordpress

bash script to create a WP environment with the correct protections.

first do:

log in as root

cd ~ ;

/usr/bin/dnf  --assumeyes  install git  ;

git clone https://github.com/edwardsmarkf/selinux-wordpress/  ;

bash -vx  ./selinux-wordpress/selinux-wordpress.bsh  > ~/selinux-wordpress.bsh.log  2>&1  &

tail -f   ~/selinux-wordpress.bsh.log   ;

also required:  (can be done after reboot

sed --in-place  --expression='s/^upload_max_filesize = 2M/;;;;&|upload_max_filesize = 512M/; s/^post_max_size = 8M/;;;;&|post_max_size = 512M/; '  /etc/php.ini ;

systemctl reload php-fpm.service  ;   ######   

