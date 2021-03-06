Changelog
=========

Release 1.2.0
~~~~~~~~~~~~~

* Exposed access to the ``timeout`` value. Each SNMP call not takes an optional
  ``timeout`` value which specifies the timeout in seconds.


Release 1.1.0
~~~~~~~~~~~~~

* :py:func:`puresnmp.bulkwalk` and :py:func:`puresnmp.bulkget` have been implemented.
* More "cookbook" examples
* :py:func:`puresnmp.walk` and :py:func:`puresnmp.table` operations now return
  pythonized values (as it should be).
* Types are now properly detected. ``NonASN1Type`` should no longer show up.
* Walking over the end of the OID tree no longer raises an exception.
* SNMP ``TimeTicks`` are now parsed into :py:class:`datetime.timedelta` instances.
* ``port`` is now optional for ``GetNext`` requests (using ``161`` by default)
* VarBinds can now only be created with ``ObjectIdentifier`` or ``str`` instances as first element.
* :py:func:`puresnmp.multiwalk` is now more generic and the backbone of both ``bulkwalk`` and ``walk``.
* Fixed issue with ReadTheDocs
* More unit tests

Internal changes for better RFC3416 conformance
###############################################

* Using real PDU "type" values (tags).
* Renamed "error_code" to "error_status".
* Added error statuses from RFC3416.
* Opaque now inherits from OctetString.
* IpAddress now inherits from OctetString.
* Added support for Counter64 values.
* Raising an error when requesting too many varbinds.
* Renamed ``puresnmp.SnmpMessage`` to :py:class:`puresnmp.PDU`

Notable bugfixes on the 1.1.x branch
####################################

* Some internal types leaked to the outside. This is no longer the case (fixed
  in ``v1.1.1``)
* Raw packets are logged using the ``DEBUG`` level ("fixed" in ``v1.1.1``).
* Fixed encoding of long length values (fixed in ``v1.1.2``)
* ``v1.1.3`` added minor internal fixes.
* Fixed IP-Address Header (fixed in ``v1.1.4``)
* Fixed signed integers (fixed in ``v1.1.5``)
