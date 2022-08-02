Solaris 9
=========

KB
--

Guides
------

Properly adding an user
~~~~~~~~~~~~~~~~~~~~~~~

Login as root, then do the following: 

::

    # groupadd wheel
    # useradd -g adm -G wheel -d /export/home/myself
    # chown -R myself:adm /export/home/myself
    # passwd myself

...assuming the user is called ``myself``.

.. admonition:: Note
    
    The ``wheel`` part is only used for convenience in case we want to install ``sudo`` later on.

Display Configuration for VirtualBox
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can either configure it correctly while installing or use ``kdmconfig`` later on to change it. 

Make sure to:

* choose "VESA Generic Driver for Vesa-Comptible Video Cards" as your video card,
* choose "Super VGA 35.5 kHz (800x600 @ 56Hz and 1024x768 Interlaced)" as your monitor,
* choose any screen size and,
* choose "1024x768 - 16777216 colors Interlaced" as your resolution and 1024x768 as your virtual resolution.

At this point you should be able to see the ``kdmconfig`` test pattern on your screen. 

QA
--

Setup
~~~~~

**Q:** The installation is stuck on "Using RPC Bootparams for network configuration information", and if I press ``Ctrl-C`` multiple times I get dropped to a prompt. What do I do?

**A:** Something went wrong in the first stage of the installation, I suggest you start over.

Networking
~~~~~~~~~~

**Q:** The system won't let me specify the hostname and FQDN if I choose to use DHCP.

**A:** Solaris, by default, performs hostname discovery. That can be turned off later on, but for the initial setup it's better to configure the network manually.

Virtual Guest
~~~~~~~~~~~~~

**Q:** The mouse behaves oddly in VirtualBox. How do I fix it?

**A:** Select "USB Tablet" instead of "PS/2 Mouse" in the VM options.

----

**Q:** Which IP should I give the machine? I'm using VirtualBox with a NAT adapter.

**A:** You can use the ``VBoxManage list dhcpservers`` command to view the address ranges for your virtual networks, then choose an IP that's outside of the range of the DHCP server (but on the same network).

Resources
---------

* `Sun/Oracle Field Engineer Handbook <https://dogemicrosystems.ca/pub/Sun/Field_Engineer_Handbook/sun-feh-2_1_sunshack.org/>`_
* `Sun/Oracle Systems Handbook <https://dogemicrosystems.ca/pub/Sun/System_Handbook/Sun_syshbk_V7.0/>`_
* `Freeware <http://download.nust.na/pub3/solaris/sunfreeware/pub/freeware/sparc/5.9/>`_
* `Companion CD <http://download.nust.na/pub3/solaris/sunfreeware/pub/freeware/companioncd/iso/>`_
