# CockroachDB-Latest Vagrant box

This is a simple base Vagrantfile to download and run the latest version of CockroachDB into a 64 bit ubuntu/trusty environment.

#### Dependencies

This box makes use of the [vagrant-reload plugin](https://github.com/aidanns/vagrant-reload).  Before starting the box, make sure you have the plugin installed by running:

    $ vagrant plugin install vagrant-reload

#### Configuration

The box will run a 3-node cockroach cluster on a single machine.  Only the first node will have its SQL and HTTP ports forwarded to the host machine.  The host environment ports that these are forwarded to can be configured with the environment variables:

- `COCKROACH_SQL_PORT` - The port used for inter-node communication, or connecting with a SQL client.
- `COCKROACH_HTTP_PORT` - The port used for the cluster administration web interface.

#### File descriptor limits

Along with installing and starting a cockroach cluster, the box performs the steps suggested [in the CockroachDB docs](https://www.cockroachlabs.com/docs/recommended-production-settings.html#increase-the-file-descriptors-limit) to increase the file descriptor limit for the processes.
