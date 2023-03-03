# selinux-wordpress

bash script to create a WP environment with the correct protections.

first do:

log in as root

cd ~ ;

/usr/bin/dnf  --assumeyes  install git  ;

git clone https://github.com/edwardsmarkf/selinux-wordpress/  ;

bash -vx  ./selinux-wordpress/selinux-wordpress-init.bsh  > ~/selinux-wordpress.bsh-init.log  2>&1  &

tail -f   ~/selinux-wordpress.bsh.log   ;



also required:  (can be done after reboot)

bash -vx  ./selinux-wordpress/max-file-size.bsh  > ~/max-file-size.bsh-init.log  2>&1  &




also this needs to be 'adjusted' when the IP number changes yet again:

mysql   --user=wpUser  --password=wpPassword  wpDb <<END;

  SELECT option_value FROM wp_options WHERE option_name IN('siteurl','home');

  UPDATE  wp_options SET option_value = 'http://192.168.123.163'  WHERE option_name IN('siteurl','home');
END


