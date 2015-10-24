Project Hosting 3.0
===================

.. revealjs:: Project Hosting 3.0
  :title-heading: h2
  :subtitle: Lance Albertson
  :subtitle-heading: h3

.. revealjs:: Session Summary

  * Brief history of FOSS hosting
  * Advances made
  * OSL Vision 2.0
  * Discuss future of FOSS hosting

.. revealjs:: Types of FOSS Hosting

  .. rst-class:: fragment

    File Hosting

    Hosted Platform Hosting

    Co-Location Hosting

    Continuous Integration Hosting

.. revealjs:: Evolution of FOSS hosting

  .. revealjs:: File hosting

    Typically FTP and/or HTTP web servers hosted by:

    * Universities (IU, MIT, OSU)
    * ISP's
    * Other orgs (Kernel.org, ISC)

  .. revealjs:: Hosted Platform hosting

    * SourceForge (1999)
    * GNU Savannah (2001)
    * LaunchPad (2004)
    * Google Code (2006)
    * Github (2008)
    * GitLab (2011)

  .. revealjs:: Co-Location Hosting

    * ISC (1994)
    * OSU Open Source Lab (2003)
    * *Anyone else?*

    .. rv_note::

      Other universities and co-location facilities would also offer services,
      but usually at a smaller scale.

      Some companies favor projects they use internally to support the community
      back.

  .. revealjs:: Continuous Integration Hosting

    * CircleCI (2011)
    * Travis CI (2012)
    * Drone.io (2014)

    .. rv_note::

      Fairly new space for FOSS hosting services. Still seeing a lot of growth
      here.

.. revealjs:: Major Advances

  .. rst-class:: fragment

    Github

    Public cloud computing

    More CDN choices (some offer free services to FOSS)

    CI testing platforms

    .. rv_note::

      Github changed everything and really pushed the fold. Public computing
      also enabled a lot of other projects more flexibility in their hosting
      needs.

      Companies like Fastly support FOSS projects by offering them either free
      or discounted FOSS access to their service.

.. revealjs:: Co-Location vs. Public Cloud

  .. csv-table::
    :header: Co-Location, Public Cloud

    More expensive, Cheaper initial costs
    Less flexible, More flexible
    Better Performance, Performance varies
    More control, Less control
    Hardware ownership, Pay for the service

  .. rv_note::

    Purely my opinion which may be wrong. Co-Location offers a lot of advantages
    and disadvantages. For some projects it works well, but many are getting
    tired of dealing with hardware issues and moving to the public or private
    cloud.

.. revealjs:: OSL Advances

  .. revealjs:: New tools and technologies

    .. rst-class:: fragment

      Virtual computing / Private Cloud

      * OpenStack
      * Ganeti
      * Containers*

      Storage Technologies

      * GlusterFS
      * Ceph*
      * Swift (S3)*

      .. rv_note::

        Started using Ganeti in 2009, and now working on offering a private
        Openstack cloud for FOSS projects. Started using OpenStack internally in
        the last year and a half. Looking at containers next.

        Been using GlusterFS for 3+ years, looking at Ceph and Swift next for
        storage technologies.

  .. revealjs:: Configuration Management

    .. rst-class:: fragment

      Chef

      Integration testing on infrastructure

      Scale up infrastructure easier

      Standardize deployments of services

      Delegate infrastructure code with projects

.. revealjs:: What do FOSS Projects Need?

  .. revealjs:: Testing Resources

    .. rst-class:: fragment

      Flexible testing compute resources

      Customizable test integration tools

      Unique testing challenges

    .. rv_note::

      Things that don't fit well with free services like TravisCI.

      TravisCI can be slow, having dedicated high performance bare metal
      hardware is important

      Some projects need to test their hardware at a larger scale to fix or find
      bugs

  .. revealjs:: Managed Service Hosting

    .. rst-class:: fragment

      Hosting complex platforms:

      Gerrit, Gitlab, Jenkins, etc

      Mailman, Jira, etc

      They need the service, but don't want to manage it

      .. rv_note::

        We get a lot of requests to host random services that can be complicated
        to host. Most are alternatives to things like Github.

  .. revealjs:: Neutral CDN Mirroring

    .. rst-class:: fragment

      Projects get popular and need to scale fast

      Current FTP mirroring infrastructure not flexible enough

      API-driven, geographically diverse

      Hosted by a trusted entity

  .. revealjs:: Access to specialized hardware

    .. rst-class:: fragment

      New and upcoming hardware (ARM64, POWER8, Open Compute, etc)

      Porting and fixing bugs

      IoT

.. revealjs:: How do we get there?

.. revealjs:: OSL Vision 2.0

  .. revealjs:: Technical Upgrade

    .. rst-class:: fragment

      Build and expand Cloud infrastructure (Ganeti & OpenStack)

      Automated Build Services

      Test Services and Support

      Project Dashboards

      OSL CDN (ftp mirroring 2.0)

      Security Audits

  .. revealjs:: OSL University Network

    .. rst-class:: fragment

      Collaborate with global universities

      Host half rack of gear

      OpenStack / Ganeti

      Mentor students at those universities

  .. revealjs:: Re-engineer backend services

    .. rst-class:: fragment

      Convert everything to Chef + CentOS

      Catch up with technology trends

      Fully testable infrastructure

      Make it more robust to failure

.. revealjs:: OSL - SuperCell

  .. revealjs:: Currently

    .. rst-class:: fragment

      Created in 2010 in conjunction with Facebook

      Utilized Ganeti to offer VM compute resources to projects

      Dozen or so projects are currently using it

  .. revealjs:: Plans

    .. rst-class:: fragment

      Rebuild with OpenStack and expand resources

      Ease on-boarding for projects

      Offer pre-built managed CI solutions

      Access to upcoming testing suites from Academia

  .. revealjs:: Education and Diversity

    .. rst-class:: fragment

      Open Source track in EECS at OSU

      Online classes targeted at DevOps topics

      Diversify the OSL workforce

      .. rv_note::

        OSU Post-Bac program is a huge success. Piggy back on that.

.. revealjs:: Summary

  .. rst-class:: fragment

    Testing resources are important to projects

    Need a place to host unique hardware

    Managed service hosting

    Increase our academic mission around DevOps and FOSS

    We need your help!

.. revealjs:: Discussion future of FOSS hosting

  .. rst-class:: fragment

    What do YOU need?

    What is missing?

    What's important to you?

    What should the OSL be doing?

.. revealjs:: Questions?

  Lance Albertson

  lance@osuosl.org

  `@ramereth`_

  http://osuosl.org

  http://lancealbertson.com

  https://github.com/ramereth/presentation-project-hosting

  *Attribution-ShareAlike CC BY-SA ©2015*

  .. raw:: HTML

    <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">
    <img alt="Creative Commons License" style="border-width:0"
    src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a>

.. _@ramereth: http://twitter.com/ramereth
