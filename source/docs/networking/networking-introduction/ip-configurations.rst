# IP Configurations

.. note:: This document describes the IP configuration used at events, both on the fields and in the pits, potential issues and workaround configurations.

## TE.AM IP Notation

The notation TE.AM is used as part of IPs in numerous places in this document. This notation refers to splitting your five digit team number into digits for the IP address octets. Where AM is the last two digits of the team number, and TE is the first three digits. Leading zeros are optional. This scheme supports team numbers up to 25599.

Example: ``10.TE.AM.2``

Team 1 - ``10.0.1.2``

Team 12 - ``10.0.12.2``

Team 122 - ``10.1.22.2``

Team 1002 - ``10.10.2.2``

Team 1212 - ``10.12.12.2``

Team 1202 - ``10.12.2.2``

Team 1220 - ``10.12.20.2``

Team 3456 - ``10.34.56.2``

Team 10000 - ``10.100.0.2``

Team 12345 - ``10.123.45.2``

## On the Field

This section describes networking when connected to the Field Network for match play

### On the Field DHCP Configuration

The Field Network runs a :term:`DHCP` server with pools for each team that will hand out addresses in the range of ``10.TE.AM.20`` to ``10.TE.AM.199`` with a subnet mask of ``255.255.255.0``, and a default gateway of ``10.TE.AM.4``.
When configured for an event, the Team Radio runs a DHCP server with a pool for devices onboard the robot that will hand out addresses in the range of 10.TE.AM.200 to 10.TE.AM.219 with a subnet mask of 255.255.255.0, and a gateway of 10.TE.AM.1.

-  Vivid-Hosting VH-109 Robot Radio - Static ``10.TE.AM.1`` programmed by
   Kiosk
-  roboRIO - DHCP ``10.TE.AM.2`` assigned by the Robot Radio
-  Driver Station - DHCP ("Obtain an IP address automatically")
   10.TE.AM.X assigned by field
-  IP camera (if used) - DHCP ``10.TE.AM.Y`` assigned by Robot Radio
-  Other devices (if used) - DHCP ``10.TE.AM.Z`` assigned by Robot Radio

.. note:: If the roboRIO is not being assigned a DHCP IP address of ``10.TE.AM.2``, ensure you've :ref:`Set the roboRIO team number <docs/zero-to-robot/step-3/roborio2-imaging:Setting the roboRIO Team Number>`

### On the Field Static Configuration

It is also possible to configure static IPs on your devices to accommodate devices or software which do not support mDNS. When doing so you want to make sure to avoid addresses that will be in use when the robot is on the field network. These addresses are ``10.TE.AM.1`` for the VH-109 radio, ``10.TE.AM.4`` for the field router, and anything ``10.TE.AM.20`` or greater which may be assigned to a device configured for DHCP or else reserved. The roboRIO network configuration can be set from the webdashboard.

-  VH-109 radio - Static ``10.TE.AM.1`` programmed by Kiosk
-  roboRIO - Static ``10.TE.AM.2`` would be a reasonable choice, subnet mask
   of ``255.255.255.0`` (default)
-  Driver Station - Static ``10.TE.AM.5`` would be a reasonable choice,
   subnet mask **must** be ``255.0.0.0`` to enable the DS to reach both the robot and :term:`FMS` Server, without additionally configuring the default gateway.
   If a static address is assigned and the subnet mask is set to ``255.255.255.0``, then the default gateway must be configured to ``10.TE.AM.4``.
-  IP Camera (if used) - Static ``10.TE.AM.11`` would be a reasonable
   choice, subnet ``255.255.255.0`` should be fine
-  Other devices - Static ``10.TE.AM.6-.10`` or ``.12-.19`` (.11 if camera not
   present) subnet ``255.255.255.0``

## In the Pits

.. note:: There is a DHCP server running on the wired side of the Robot Radio in the event configuration.

### In the Pits DHCP Configuration

-  VH-109 radio - Static ``10.TE.AM.1`` programmed by Kiosk.
-  roboRIO - ``10.TE.AM.2``, assigned by Robot Radio
-  Driver Station - DHCP ("Obtain an IP address automatically"),
   ``10.TE.AM.X``, assigned by Robot Radio
-  IP camera (if used) - DHCP, ``10.TE.AM.Y``, assigned by Robot Radio
-  Other devices (if used) - DHCP, ``10.TE.AM.Z``, assigned by Robot Radio

.. note:: If the roboRIO is not being assigned a DHCP IP address of ``10.TE.AM.2``, ensure you've :ref:`Set the roboRIO team number <docs/zero-to-robot/step-3/roborio2-imaging:Setting the roboRIO Team Number>`

### In the Pits Static Configuration

It is also possible to configure static IPs on your devices to accommodate devices or software which do not support mDNS. When doing so you want to make sure to avoid addresses that will be in use when the robot is on the field network. These addresses are ``10.TE.AM.1`` for the VH-109 radio and ``10.TE.AM.4`` for the field router.
