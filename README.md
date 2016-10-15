# CockroachDB-Latest Vagrantfile

This is a simple Vagrantfile to download and run the latest version of [CockroachDB](https://github.com/cockroachdb/cockroach) into a 64 bit ubuntu/trusty environment using VirtualBox.

#### Running

This Vagrantfile makes use of the [vagrant-reload plugin](https://github.com/aidanns/vagrant-reload).  Before starting the box, make sure you have the plugin installed by running:

    $ vagrant plugin install vagrant-reload

The base box used in this Vagrantfile is VirtualBox based, so make sure you have [VirtualBox](https://www.virtualbox.org) installed as well.

Once these two prerequisites are met, you should be able to run the box by navigating to the directory containing the Vagrantfile and running:

    $ vagrant up

#### Configuration

The box will run a 3-node cockroach cluster on a single machine.  Only the first node will have its SQL and HTTP ports forwarded to the host machine.  The host environment ports that these are forwarded to can be configured with the environment variables:

- `COCKROACH_SQL_PORT` - The port used for inter-node communication, or connecting with a SQL client.
- `COCKROACH_HTTP_PORT` - The port used for the cluster administration web interface.

#### File descriptor limits

Along with installing and starting a cockroach cluster, the box performs the steps suggested [in the CockroachDB docs](https://www.cockroachlabs.com/docs/recommended-production-settings.html#increase-the-file-descriptors-limit) to increase the file descriptor limit for the processes.
