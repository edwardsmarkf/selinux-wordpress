# selinux-wordpress

bash script to create a WP environment with the correct protections.

first do:

log in as root

cd ~ ;

/usr/bin/dnf  --assumeyes  install git  ;

git clone https://github.com/edwardsmarkf/selinux-wordpress/  ;

bash -vx  ./selinux-wordpress/selinux-wordpress.bsh  > ~/selinux-wordpress.bsh.log  2>&1  &

tail -f   ~/selinux-wordpress.bsh.log   ;
