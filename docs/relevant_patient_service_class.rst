.. _relpat_sops:

Relevant Patient Information Query Service Class
================================================
The `Relevant Patient Information Query Service Class
<http://dicom.nema.org/medical/dicom/current/output/html/part04.html#chapter_Q>`_
defines a service that facilitates querying of stored Instances for specific
information from a single patient.


.. _relpat_sops:

Supported SOP Classes
---------------------

+-----------------------------+----------------------------------------------+
| UID                         | SOP Class                                    |
+=============================+==============================================+
| 1.2.840.10008.5.1.4.37.1    | GeneralRelevantPatientInformationQuery       |
+-----------------------------+----------------------------------------------+
| 1.2.840.10008.5.1.4.37.2    | BreastImagingRelevantPatientInformationQuery |
+-----------------------------+----------------------------------------------+
| 1.2.840.10008.5.1.4.37.3    | CardiacRelevantPatientInformationQuery       |
+-----------------------------+----------------------------------------------+


.. _relpat_statuses:

Statuses
--------

C-FIND Statuses
~~~~~~~~~~~~~~~~

+------------+----------+----------------------------------+
| Code (hex) | Category | Description                      |
+============+==========+==================================+
| 0x0000     | Success  | Success                          |
+------------+----------+----------------------------------+
| 0x0122     | Failure  | SOP Class not supported          |
+------------+----------+----------------------------------+
| 0xFE00     | Cancel   | Processing has been terminated   |
+------------+----------+----------------------------------+


Relevant Patient Information Query Service Statuses
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------------+----------+----------------------------------------------+
| Code (hex)       | Category | Description                                  |
+==================+==========+==============================================+
| 0xA700           | Failure  | Out of resources                             |
+------------------+----------+----------------------------------------------+
| 0xA900           | Failure  | Identifier does not match SOP Class          |
+------------------+----------+----------------------------------------------+
| 0xC000           | Failure  | Unable to process                            |
+------------------+----------+----------------------------------------------+
| 0xC100           | Failure  | More than one match found                    |
+------------------+----------+----------------------------------------------+
| 0xC200           | Failure  | Unable to support requested template         |
+------------------+----------+----------------------------------------------+
| 0xFF00           | Pending  | Matches are continuing                       |
+------------------+----------+----------------------------------------------+

pynetdicom Relevant Patient Information Query Statuses
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When pynetdicom is acting as a Relevant Patient Information SCP it uses the
following status codes values to indicate the corresponding issue has occurred
to help aid in debugging.

+------------------+----------+-----------------------------------------------+
| Code (hex)       | Category | Description                                   |
+==================+==========+===============================================+
| 0xC001           | Failure  | User's callback implementation returned a     |
|                  |          | status Dataset with no (0000,0900) *Status*   |
|                  |          | element                                       |
+------------------+----------+-----------------------------------------------+
| 0xC002           | Failure  | User's callback implementation returned an    |
|                  |          | invalid status object (not a pydicom Dataset  |
|                  |          | or an int)                                    |
+------------------+----------+-----------------------------------------------+
| 0xC310           | Failure  | Failed to decode the dataset received from    |
|                  |          | the peer                                      |
+------------------+----------+-----------------------------------------------+
| 0xC311           | Failure  | Unhandled exception raised by the user's      |
|                  |          | implementation of the ``on_c_find`` callback  |
+------------------+----------+-----------------------------------------------+
| 0xC312           | Failure  | Failed to encode the dataset received from    |
|                  |          | the user's implementation of the ``on_c_find``|
|                  |          | callback                                      |
+------------------+----------+-----------------------------------------------+


References
----------

* DICOM Standard, Part 4, `Annex Q <http://dicom.nema.org/medical/dicom/current/output/html/part04.html#chapter_Q>`_
* DICOM Standard, Part 7, Section
  `9.1.2.1.5 <http://dicom.nema.org/medical/dicom/current/output/chtml/part07/chapter_9.html#sect_9.1.2.1.5>`_
* DICOM Standard, Part 16, Annex A, `TIDs 9000-9007 <http://dicom.nema.org/medical/dicom/current/output/chtml/part16/sect_RelevantPatientInformationTemplates.html>`_
