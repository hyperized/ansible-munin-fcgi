Role Name
=========

Munin monitoring server with Nginx config, running FCGI for Ubuntu with upstart

Requirements
------------

Ubuntu with Upstart is required

Role Variables
--------------

	munin_packages:
  	- python-passlib
  	- munin
  	- autoconf
  	- perl
  	- libxml-parser-perl
  	- ruby
  	- spawn-fcgi
  	- libcgi-fast-perl

	munin_dbdir: /var/lib/munin
	munin_logdir: /var/log/munin
	munin_rundir: /var/run/munin

	munin_conf_d_directory: /etc/munin/munin-conf.d
	munin_htmldir: /var/cache/munin/www
	munin_includedir: /etc/munin/munin-conf.d

	munin_graph_strategy: cgi
	munin_html_strategy: cgi
	munin_cron_job: present

	munin_max_processes: 16

	munin_admin_user: munin
	munin_admin_password: munin

	munin_alerts:
  	- {
    	    name: "Your name",
    	    email: "Your_mail@your_domain.tld",
    	    subject: "Munin-notification for ${var:group} :: ${var:host}",
    	    level: "warning critical"
   	}

Dependencies
------------

Nginx config is provided, nginx itself is not included.

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: hyperized.munin-fcgi }

License
-------

MIT

Author Information
------------------

Gerben Geijteman - DevOps FD Mediagroep BV.
http://werkenbijfdmg.nl
