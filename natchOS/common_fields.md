Common Fields
Every entity has it own set of predefined fields, which are documented per entity in their file definition. But there are some common fields that will be found in many entities. 



File based import and Plankton
These fields can be found in both the file based import and the web API RESTful service.



~Code 

Fields with Code as suffix;  the unique key of the entity as known in the master data. See below for more information about keys/codes.



InternalName 

A unique internal/private name for the record of an entity; this identifies the entity in a human readable way; will not be displayed publicly



LCID 

The Language Code Identifier. Defines the language and country of a record (ie. Product translation).

Records must be supplied for every language and country combination your application will be available in. Even if the data is the same for a language in multiple countries.

The most common values:

2067 = nl-be = Dutch - Belgium
2060 = fr-be = French - Belgium
1043 = nl-nl = Dutch - Netherlands
1036 = fr-fr = French - France
2057 = en-gb = English - Great Britain
1031 = de-de = German - Germany
(Google 'LCID' for complete list)



Misc XML

Data that can not be placed in the predefined fields can be placed inside XML in this field.

A root node is required.
By convention, node names should be lowercased. This is to avoid confusion (ie. camel casing vs pascal casing).
Text values must be encoded to ensure correct XML, ie. HTML or reserved characters.
Numerical values must be formatted in invariant culture. No thousand separators and "." as decimal separator.
Date values must be formatted as ISO 8601: YYYY-MM-DD.
Boolean values must be specified as 1 or 0.
<root><htmlvalue>value &lt;with html&gt;</htmlvalue><anotherfield>1</anotherfield></root>
Misc JSON

See Misc XML, but formatted as JSON.



CountryISO

The two-letter ALPHA-2 ISO 3166 notation of the country code.

More info at [www.iso.org](https://www.iso.org/iso-3166-country-codes.html).



File based imported only


The fields are specific for the file based import



Action 

Value I indicated INSERT command (processed as upsert).
Value U indicates UPDATE command (processed as upsert).
Value D indicates DELETE command (only values for key field and action field are required).
Delete only makes sense for incremental delivery; full delivery should always use Insert or Update.
Not applicable for child files.


PhoneNumberTypeID

ID that indicates the type.

1 = phone
2 = fax; if you still live in 1999
3 = mobile


SpatialLocation 

Latitude and longitude of a location. 

Formatted as <lat>,<long>
Period as decimal separator
Example: 51.09644,3.83194 for Lochristi, Belgium


About unique keys - code fields
If master data does not have a unique key or the key consists of multiple fields, a single key must be created by joining fields together to create a unique key. To ensure a unique key is created out of multiple fields, a common technique is to use a separator between the fields, ie. pipe symbol (ASCII 124).

An example for a shipping address of a customer. The key for the customer is 'CC654'. The shipping address does not have a unique key, but is unique for the customer as '001'. The shipping address key would be 'CC654|001'.



Keys must be unique in a single file.



Metadata
Data that is stored in NatchOS and managed by Natch is called metadata. Contact us for more information.

