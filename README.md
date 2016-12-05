andrewrothstein.binpack
=========

A collection of executables to be installed in a target directory

Requirements
------------

See [meta/main.yml](meta/main.yml)

Role Variables
--------------

See [var/main.yml](vars/main.yml) and [test.yml](test.yml)

Dependencies
------------

See [meta/main.yml](meta/main.yml)

Example Playbook
----------------

To be derived for concrete roles.

```yml
- hosts: servers
  roles:
    - role: andrewrothstein.binpack
	  binpack_install_dir: /usr/local/bin
	  binpack_app: myapp
	  binpack_app_ver: v1.0.0
	  binpack_files:
	    - f: foo.sh
		- f: bar.sh
	  binpack_templates:
	    - f: bing.sh
		- f: baz.sh
```

Would be similar to
```bash
mkdir -p /usr/local/bin/myapp-v1.0.0
cp files/foo.sh /usr/local/bin/myapp-v1.0.0/foo.sh
cp files/bar.sh /usr/local/bin/myapp-v1.0.0/bar.sh
templatize templates/bing.sh.j2 > /usr/local/bin/myapp-v1.0.0/bing.sh
templatize templates/baz.sh.j2 > /usr/local/bin/myapp-v1.0.0/baz.sh

ln -s /usr/local/bin/foo.sh /usr/local/bin/myapp-v1.0.0/foo.sh
ln -s /usr/local/bin/bar.sh /usr/local/bin/myapp-v1.0.0/bar.sh
ln -s /usr/local/bin/bing.sh /usr/local/bin/myapp-v1.0.0/bing.sh
ln -s /usr/local/bin/baz.sh /usr/local/bin/myapp-v1.0.0/baz.sh
```

License
-------

MIT

Author Information
------------------

Andrew Rothstein andrew.rothstein@gmail.com
