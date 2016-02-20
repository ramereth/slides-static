.. revealjs:: Openstack at OSUOSL

.. revealjs::

  .. revealjs:: About me

    Director, OSU Open Source Lab

    Sysadmin, hacker, jazz trumpet

    Gentoo, CentOS, Ganeti, OpenStack, etc

  .. revealjs:: What we do

    Infrastructure hosting for many FOSS projects

    Employ undergraduate students to learn devops

    Host 150 FOSS projects (closer to 1,000!)

    Private cloud, co-location, mirroring

.. revealjs:: Openstack History and Adventure

.. revealjs::

  .. revealjs:: So why Openstack?

    .. rst-class:: fragment

      Large Ganeti users

      Works great for pet VMs, not so much on cattle

      Needed a flexible and elastic environment for testing

      Projects are requesting more flexible computing resources

      Experience for students and staff

  .. revealjs:: The beginning

    .. rst-class:: fragment

      August 2013

      Havana Release

      Packstack

      Puppet

      Chef

      Icehouse

  .. revealjs:: Config Setup

    .. rst-class:: fragment

      Ganeti VM as controller node

      Shared bare-metal db server

      One Physical Node

      CentOS 6

  .. revealjs:: Services enabled

    .. rst-class:: fragment

      Compute

      Nova Networking (flat)

      Glance

      Keystone

      Horizon

.. revealjs:: Current use

  .. rst-class:: fragment roll-in

    Chef Integration Testing

    Test Kitchen

    Multi-node testing

    Staging applications and sites

    System Admin Class at OSU

    OpenPOWER-based cluster

    No production services (yet)

.. revealjs:: Clusters

  .. rst-class:: fragment

    x86 prod

    x86 testing

    Student Cloud (sysadmin class / DevOps Bootcamp)

    ppc64/pp64le prod

    ppc64/ppc64le testing

.. revealjs:: Deployment with Chef

  * `Chef on OpenStack`__
  * `OpenStack Official Chef Project`__
  * `Example Chef Repo for OpenStack`__
  * Split out into multiple cookbooks

    * compute, networking, etc

.. __: https://docs.chef.io/openstack.html
.. __: https://launchpad.net/openstack-chef
.. __: https://github.com/openstack/openstack-chef-repo

.. revealjs:: OpenStack Chef Repo

  * Split out into dozens of roles
  * Was difficult to figure out who to glue it all together
  * Vagrant testing environments:

    * All-in-One
    * Multi-host Neutron

  * Uses `Chef Provisioning`__ for testing with vagrant

.. __: https://github.com/chef/chef-provisioning

.. revealjs:: Testing with Vagrant

  .. rv_code::

    $ git clone https://github.com/openstack/openstack-chef-repo.git
    $ cd openstack-chef-repo
    $ chef exec rake berks_vendor
    $ chef exec rake allinone
    $ cd vms
    $ vagrant ssh controller
    $ sudo su -

.. revealjs:: osl-openstack

  * OSL Wrapper Cookbook
  * Took the roles from the OpenStack Chef Repo and converted them into recipes
  * Testing

    * Test Kitchen for individual recipes
    * Chef Provisioning environment

  * https://github.com/osuosl-cookbooks/osl-openstack

.. revealjs:: Test Kitchen

  .. raw:: html

    <blockquote>"An integration tool for developing and testing infrastructure
    code and software on isolated target platforms"</blockquote>

.. revealjs:: Test Kitchen

  * Primarily used with Chef, but can also be used with Puppet, Ansible, etc
  * Uses Vagrant by default, but we use it with OpenStack
  * ServerSpec for integration testing
  * Not the best for multi-node test integration testing

.. revealjs:: Multi-Node Testing

  Using OpenStack to test OpenStack ...

  .. rv_code::

    $ chef gem install chef-provisioning chef-provisioning-fog
    $ export CHEF_DRIVER="fog:OpenStack"
    $ export CONTROLLER_OS="CentOS 7.1"
    $ export COMPUTE_OS="CentOS 7.1"
    $ rake berks_vendor
    $ rake controller_compute

.. revealjs:: Chef Provisioning Code

  .. rv_code::

    require 'chef/provisioning'

    controller_os = ENV['CONTROLLER_OS'] || 'chef/centos-7.1'
    compute_os = ENV['COMPUTE_OS'] || 'chef/centos-7.1'
    controller_ssh_user = ENV['CONTROLLER_SSH_USER'] || 'centos'
    compute_ssh_user = ENV['COMPUTE_SSH_USER'] || 'centos'
    flavor_ref = ENV['FLAVOR'] || 3

    unless ENV['CHEF_DRIVER'] == 'fog:OpenStack'
      require 'chef/provisioning/vagrant_driver'
      vagrant_box controller_os
      vagrant_box compute_os
      with_driver "vagrant:#{File.dirname(__FILE__)}/../../../vms"
    end

    machine 'controller' do
      machine_options vagrant_options: {
        'vm.box' => controller_os
      },
                      bootstrap_options: {
                        image_ref: controller_os,
                        flavor_ref: flavor_ref,
                        key_name: ENV['OS_SSH_KEYPAIR']
                      },
                      ssh_username: controller_ssh_user,
                      floating_ip_pool: ENV['OS_FLOATING_IP_POOL']

      ohai_hints 'openstack' => '{}'
      add_machine_options vagrant_config: <<-EOF
    config.vm.network "private_network", ip: "192.168.60.10"
    config.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.cpus = 2
    end
    EOF
      role 'openstack_provisioning'
      recipe 'osl-openstack::ops_database'
      recipe 'osl-openstack::controller'
      recipe 'openstack-integration-test::setup'
      file('/etc/chef/encrypted_data_bag_secret',
           File.dirname(__FILE__) +
           '/../default/encrypted_data_bag_secret')
      converge true
    end

.. revealjs:: Testing Deployment Phases

  #. Per recipe Test Kitchen testing
  #. Multi-node testing on OpenStack with Chef Provisioning
  #. Multi-node testing on bare-metal with Chef Provisioning
  #. Deployment on Production

.. revealjs:: OpenPOWER (POWER8) OpenStack

  * Collaborated with IBM to build a POWER8 OpenStack cluster for FOSS
    developers
  * Internal IBM had developed a Fedora-clone called PowerKVM with OpenStack
  * I charged IBM to allow the OSL to build a vanilla Fedora based cluster
  * Forced IBM to ensure patches were making it upstream to libvirt, OpenStack,
    and KVM
  * Provided an interesting challenge using Fedora in "production"
  * No Chef support on ppc64 (at the time)

.. revealjs:: Current P8 Setup

  * Fedora 20 (ppc64) on compute nodes
  * CentOS 6 (x86_64) VM for controller node
  * Icehouse
  * Guest support for ppc64 and pp64le
  * Patched versions of:

    * Linux Kernel
    * libvirt
    * kvm

.. revealjs:: Guest Images: Packer FTW!

  * Utilize `Packer`__ for building images
  * We `forked`__ the `Chef Bento`__ repository
  * Add OSL specific stuff
  * Use Packer for building Ganeti images too
  * Build Chef into the images
  * Building Packer on ppc64 was ... a pain

.. __: http://packer.io
.. __: https://github.com/osuosl/bento
.. __: https://github.com/chef/bento

.. revealjs:: Future Plans

  * Upgrade to latest release (Liberty possibly)
  * Upgrade everything to CentOS 7 (including P8 systems)
  * Switch to Neutron networking
  * Switch to ppc64le on compute nodes

.. revealjs:: Questions?

  Lance Albertson

  lance@osuosl.org

  `@ramereth`_

  osuosl.org

  lancealbertson.com

  github.com/ramereth/presentation-osuosl-openstack

  *Attribution-ShareAlike CC BY-SA ©2015-2016*

  .. raw:: HTML

    <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">
    <img alt="Creative Commons License" style="border-width:0"
    src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a>

.. _@ramereth: http://twitter.com/ramereth

