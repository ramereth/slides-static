DevOps for University Students
==============================

:author: Lance Albertson
:title: Director / Sysadmin
:company: OSU Open Source Lab
:email: lance@osuosl.org
:twitter: @ramereth

*Attribution-ShareAlike CC BY-SA ©2014*

.. toctree::
  :hidden:

  proposal

About me
--------

- OSU Open Source Lab Director
- Systems Admin background
- Been at OSL since 2007
- Experienced in:

  - Virtualization (Ganeti/KVM)
  - cfengine, puppet, chef
  - CentOS/Gentoo
  - Mentoring students
- Gentoo Developer

Session Overview
----------------

.. rst-class:: build

- Current Learning Environment
- OSL Student Experience
- Devops Bootcamp
- Next Steps

Current Learning Environment
============================

There be dragons!

Theory vs. Applied
------------------

- More focus on theory than applied

  - Classwork rarely mimics real-world
  - Difficult to apply theory

.. figure:: _static/xkcd-171-string-theory.png
  :align: center
  :scale: 90%

Student Jobs
------------

*Finding experience on campus*

- Limited roles and access
- Limited availability 
- No structure

.. figure:: _static/osl-noc2.jpg
  :align: center
  :scale: 60%

Insufficient Mentoring
----------------------

- No dedicated staff/faculty
- LUG's help, but not the solution 
- No centralized program

  - Need a place for advanced students to excel more
  - Also need an environment for *"newbies"*

OSL Student Experience
======================

Giving students real-world experience and mentorship

OSL Overview
------------

- Provide hosting for FOSS projects
- Services we provide

  - Co/Location
  - Virtualization (Cloud)
  - Managed/Unmanaged hosting
  - Email, DNS, mailing list, etc
- Development focused on supporting hosting
- Media communications team

OSL NOC
-------

.. figure:: _static/osl-noc.jpg
  :align: center
  :scale: 80%

OSL Student Experience
----------------------

- Given full *"root"*
- Spend six months mentoring

  - Mix of full-timer and senior student mentorships
- Work on support tickets and customers
- Interact with people internationally
- Ownership of a project
- Treated like a full-timer

Scaling problem
---------------

.. rst-class:: build

- Balancing FTE to Student ratios
- A lot of time and resource is put in mentoring
- Represent less than 1% of total OSU CS population
- Budget constraints on hiring more students

DevOps Bootcamp
===============

Expanding DevOps beyond the OSL...

http://devopsbootcamp.osuosl.org

Portland State *"Braindump"*
----------------------------

- Weekly meet up to teach being sysadmin
- In-depth teaching on specific topics (DNS, Apache, etc)
- Graduated system

  - Start out with helpdesk support
  - Get "non-root" access to systems
  - "Rooter"
- Year long program

  - Starts out with 60+ end up with ~10 solid recruits

Adapt PSU's Braindump
---------------------

Making it work for the OSL and OSU .. and DevOps Bootcamp was born!

**Goals:**

.. rst-class:: build

- Teach basic system administration skills
- Introduce FOSS development
- Publicize all the content
- Eventually integrate into EECS program

Program Structure
-----------------

- Weekly meet ups about a specific topic
- Weekly content planning meetings
- Simple *homework* each week
- Both lecture and hands on
- Communication

.. figure:: _static/dobc.jpg
  :align: right
  :scale: 60%

..

  - Mailing list
  - IRC
  - LUG

Tools
-----

.. rst-class:: build

- Vagrant

  - CentOS/Debian VMs
- Github
- Sphinx-doc and Read The Docs

  - Hieroglyph for slides
- Google Hangouts Live (for recording)

Curriculum
----------

- Linux Basics
- Basic System Administration
- Basic FOSS Development Methodologies
- Base infrastructure services for any organization
  
  - DNS, Email, web server, database servers, etc
- Building a mock infrastructure for a mock company from top to bottom
- Content based from `CS312 Sysadmin class`_
  
  - *last taught in 2009*

.. _CS312 Sysadmin class: http://osuosl.org/students/cs312

Topics discussed so far
-----------------------

.. rst-class:: build

- **The Basics:** Shell, file permissions, package management
- Editors and git
- Scripting & Troubleshooting
- Services and deploying a web app
- Boot process and filesystem hierarchy
- Databases
- Security & Authentication

.. figure:: _static/xkcd_838.png
  :align: center 
  :scale: 60%

Building a mock infrastructure
------------------------------

- Build a breakable infrastructure

  - Best to learn from real-world experience
  - But not production (yet)
- Basic services:
  
  - DNS, Email, web, database, etc
- Develop a basic webapp collaboratively
- Utilize configuration management (puppet / chef)
- Use the cloud (i.e. OpenStack, AWS, etc)

Feedback
--------

- Attendance

  - First meeting: 34
  - Other meetings: 10-20
- Format seems to work
- Vagrant and Virtualbox can be a PITA
- Recording using Google Hangouts is great (but buggy)
- Having everything in git is awesome
- It takes a long time to make content
- We started way too late
- Learn to be flexible
- K.I.S.S.

Next Steps
==========


Plans
-----
- Continue to build more content *(and tweak it)*
- Develop new curriculum in EECS program

  - Create a side track focused on DevOps
- Include outside speakers from the industry
- Include contributions from external sources

  - Because, FOSS!

Questions?
==========

:name: Lance Albertson
:company: OSU Open Source Lab
:email: lance@osuosl.org
:twitter: @ramereth @osuosl
:blog: http://lancealbertson.com
:devopsbootcamp: http://devopsbootcamp.osuosl.org
:github: https://github.com/devopsbootcamp


*Attribution-ShareAlike CC BY-SA ©2014*
