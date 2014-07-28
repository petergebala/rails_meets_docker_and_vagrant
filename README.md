## Example application for rails integration with vagrant and docker

#### Usage

1. Download repository
2. Install vagrant and docker on you os
3. Copy you public ssh key to app dir (needed for ssh key based authentication)
4. Run `vagrant up postgres --provider=docker`
5. Run `vagrant up rails --provider=docker`
6. Attach to rails app: `docker attach example_rails` or connect via ssh: `vagrant ssh rails`
7. Then do what you want. Run server, execute rake tasks, run tests.


#### Additional Information

Check docker and vagrant documentation.
Docker files repositories:
- [docker_rails] (http://github.com/petergebala/docker_rails)
- [docker_postgres] (http://github.com/petergebala/docker_postgres)
