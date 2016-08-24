# NginX

By default, the server binds to port 80. If installed in a Gateway server should be binding on port 8080 as HAProxy is by default on port 80.

To define the port change the var "nginx_port" in group_vars or host_vars.