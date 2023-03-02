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

sed --in-place --file=- /etc/php.ini << END;
s/^upload_max_filesize = 2M/;;;;&\nupload_max_filesize = 512M/; s/^post_max_size = 8M/;;;;&\npost_max_size = 512M/;
END

systemctl reload php-fpm.service  ;   ######   


also this needs to be 'adjusted' when the IP number changes yet again:

mysql   --user=wpUser  --password=wpPassword  wpDb <<END;
    UPDATE  wp_options SET option_value = 'http://192.168.123.163'  WHERE option_name IN('siteurl','home');
END


