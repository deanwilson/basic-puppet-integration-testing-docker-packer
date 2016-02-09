# Basic Puppet integration testing with Docker and Packer #

A small repo to show an example of running integration tests against a
puppet module. Assumes you have Packer and Docker installed and working.

This code is based on the [Puppet integration tests in (about) seven minutes](http://www.unixdaemon.net/puppet/puppet-integration-tests-in-seven-minutes/) blog post.

    ./packer validate strace-testing.json

    ./packer build strace-testing.json

    ==> docker: Pulling Docker image: ubuntu
    ...
        # puppet output
        docker: Notice: /Stage[main]/Strace/Package[strace]/ensure: ensure changed 'purged' to 'present'
        docker: Info: Creating state file /var/lib/puppet/state/state.yaml
        docker: Notice: Finished catalog run in 8.59 seconds
    ...
        # goss output
    ==> docker: Provisioning with shell script: /tmp/packer-shell193374970
        docker: Package: strace: installed: matches expectation: [true]
        docker:
        docker:
        docker: Total Duration: 0.009s
        docker: Count: 1, Failed: 0


### Author ###
[Dean Wilson](http://www.unixdaemon.net)
