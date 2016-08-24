# Users
This role manages the system users and ssh access. All EH users have "webdev" as their main group and have access to SUDO. File permissions are overridden by ACL using the "webdev" group, so that any user can upload a website to /srv/websites/. All users are created with a random, unknown password, as they should not need it. Updating the user password is only possible (at the moment) by logging in the actual server and running CLI commands.

If we add additional groups the "nginx" role needs to be updated, to run the correct setfacl command.

SSH access only allows the usage of key - no user/password. 

## SSH Keys
Keys are stored in /files. A reference to the key should be provided in the config vars

## Vars
A full list of users should be ALWAYS maintained in defaults/main.yml and (if necessary) in /group_vars or /host_vars. The later ones override the default list completely - no merge of the lists of users is performed.

Failing to keep a full list in all the vars locations will mean that some boxes may end up with a set of users that doesn't match the list in the var file, as absence from the file does not remove a user from the system. The default list in defaults should be the more conservative one with the minimum set of grants. In case of doubt deleting the additional lists should ensure the servers are secure.

"state" determines if the user exists in the box. I guess we shouldn't remove users that have made changes in that box, but either remove their ssh access

"key_state" determines if the user has ssh access to the box
