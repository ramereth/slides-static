Cloud Images with Packer
========================

Lance Albertson
OSU Open Source Lab

Cloud Image Hell
----------------

.. image:: _static/clouds.jpg
  :width: 50%
  :align: center

* Most distros provide their own image today
* Building your own for security and customization
* Different tool for each os/cloud platform

Packer
======

.. image:: _static/packer-logo.png
  :width: 60%
  :align: center

http://packer.io

* Machine image building tool created by Mitchell Hashimoto (of Vagrant fame)
* Unifies building of images across multiple platforms

Supported Platforms
===================

.. csv-table::

  Amazon EC2, Digital Ocean
  Docker, GCE
  Openstack, Parallels
  QEMU (kvm), Virtual Box
  VMWare

Building the Image
------------------

Building a kvm OpenStack Image:

.. rst-class:: codeblock-sm

::

  $ packer build centos-7.0-x86_64-openstack.json
  qemu output will be in this color.

  ==> qemu: Downloading or copying ISO
      qemu: Downloading or copying: http://centos.osuosl.org/7.0.1406/isos/x86_64/CentOS-7.0-1406-x86_64-NetInstall.iso
  ==> qemu: Creating hard drive...
  ==> qemu: Starting HTTP server on port 8081
  ==> qemu: Found port for SSH: 3213.
  ==> qemu: Looking for available port between 5900 and 6000
  ==> qemu: Found available VNC port: 5947
  ==> qemu: Starting VM, booting from CD-ROM
      qemu: WARNING: The VM will be started in headless mode, as configured.
      qemu: In headless mode, errors during the boot sequence or OS setup
      qemu: won't be easily visible. Use at your own discretion.
  ==> qemu: Overriding defaults Qemu arguments with QemuArgs...
  ==> qemu: Waiting 10s for boot...
  ==> qemu: Connecting to VM via VNC
  ==> qemu: Typing the boot command over VNC...
  ==> qemu: Waiting for SSH to become available...

Bento
-----

https://github.com/chef/bento

* Chef's Packer template and script repository for building their vagrant boxes
* Covers most platforms you care about
* Figured out the hard stuff for you!
* Great place to see how to see Packer examples
* Checkout our fork: https://github.com/osuosl/bento/
