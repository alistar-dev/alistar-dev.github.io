# Import - Text Files
NatchOS offers an out-of-the-box import for plain text files.

## TABLE OF CONTENTS

- FILE REQUIREMENTS
- FILE LAYOUT GUIDELINES
- FILE NAMING
- INCREMENTAL / FULL DELIVERY
  - Incremental
  - Full delivery
- DATA
  - Fields
  - Main file
  - Optional child file
- DATA TYPES
- METADATA
- ENTITIES

## FILE REQUIREMENTS
The files must match the following criteria:

- Flat file in TXT file type
- Single entity per file, optional extra file for child entities (ie. Product and product translations)
- Header record is required, even if there is no data
- Child files are required, with header record, even if there is no data
- UTF8 encoding
- Field separator must be used, no fixed length fields
- Numeric values must be consistently formatted in the same culture
- Date values must be formatted as YYYYMMDD, ie. 25th of May 1977 is 19770525 
- Time values must be formatted as hh:mm:ss, ie. 13:05:00
- Use a text qualifier
- Required fields must be supplied or a default value must be configured
- May not contain blank lines, except for the last line

## FILE LAYOUT GUIDELINES
These guidelines are highly recommended:

- File compressed into ZIP
  - Child file should be zipped together with parent file - this ensures delivery of both files at the same time
  - Zip files may be password protected. The password length must be between 8 and 1000 characters. Supported encryptions are ZipCrypto and AES-256.
- Field delimiter is TAB (ASCII 9)
- Text qualifier is double quotes (ASCII 34)
- Use invariant culture (LCID 127) for numeric values, for example 3.1415 for Pi
- Each record should contain the same number of fields

## FILE NAMING
We have a naming convention for files, that consists of 3 parts, that are joined by an underscore.

9 or 14 digits for the ID of the entity
This number should increment (gaps allowed) with every (parent) file
Child file must have the same ID
Can represent a date/time/timestap, but is not required
Entity name (either predefined or custom)
Incremental or full delivery flag, using one of these 2 values: incr, full. (not for all projects)

=> 20220407123059_customer_full.txt

=> 22040712301122_product_incr.txt

=> 000000022_product_full.txt and 000000022_productml_full.txt zipped into 000000022_product_full.zip

## INCREMENTAL / FULL DELIVERY
The files can be processed as an incremental delivery or as a full delivery.

**Incremental**

These files are small and contain only changes since the previous delivery of the entity.
Processing is fast and is possible during business hours.
Only the records in the file are inserted, updated or deleted.

**Full delivery**

These files contain all the data of the entity.
Processing may be slow and is only available during off-peak hours.
Live data is replaced by the records in the file. This will result in a delete of existing records that were not supplied in the file.

We have a protection against deleting too many records in case we process a file with not enough records. This protection check the percentage of records that will be deleted against a defined threshold, ie. 50% or 90%. This is currently implemented for full delivery only, but will also be added to incremental delivery in the future.

Incremental and full delivery may be mixed for an entity. Ie. A full delivery during the weekend, and incremental deliveries during the week.

## DATA

**Fields**

Every entity has it own set of predefined fields, which are documented per entity in their file definition. But there are some **common fields** that will be found in multiple files. [Check the Common Fields page for more information.](./common_fields)

**Main file**

Contains records per entity (ie. Product, Category), or link between entities (ie. The many-to-many category-product combination).

**Optional child file**

Contains child records of the parent. This is a one-to-many relation. Ie. 1 customer can have multiple phone numbers.

## DATA TYPES

- Text / (n)varchar / (n)char: surround with text qualifier; if the value contains the text qualifier, it must be escaped (ie. double quotes must be replaced by two double quotes
- Number / int / decimal: integer or decimal in invariant culture
- Bool(ean) / bit: 0 or 1
- Date: YYYYMMDD
- XML: Fields/nodes must be placed within a single parent node.
- JSON: Json representation of data
An example with headers

`"Code"    "Name"    "Boolean"    "Date"    "Misc"
"ent001"    "name ""in quotes"" here"    1    "20201231"    "<root><value>some value</value><num>5</num></root>"`


## METADATA
Data that is stored in NatchOS and managed by Natch is called metadata. Contact us for more information.


## ENTITIES
Check your Admin Platform to see the configured entities with details about the file.
