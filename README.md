SAML SCHEMA
==============

## DESCRIPTION
This project contains *slightly* adjusted copies of the SAML protocol schema files 
(and their dependencies) created and originally published by OASIS and W3C.

The files are presented here as a convenience for both DIL and others, especially
as a source for integrating into other projects using Git and Github.

## DERIVATION
The official source of SAML protocol documentation and schemas is here:

  http://docs.oasis-open.org/security/saml/v2.0/
  
This repository is based on InCommon's versions of the official files:

  http://wayf.incommonfederation.org/bridge/docs/

If you want the official, purest, most recent schema files do not use the files in
this repository: use the official files. 

## ADDITIONAL FEATURES
As few as possible! Any significant changes to the schema will break compatibility
with the official SAML protocol and cause no end of problems. 

* Schema have been tweaked by InCommon to work when accessed on a local filesystem,
rather than over the Internet. This makes processes such as verifying SAML metadata
much faster and much more resilient.
* The X509SerialNumber type has been changed to work around a problem caused by
some Certificate Authorities issuing certificates with huge random serial numbers
that exceed the capacity of some some schema validation software.

### Adaption for offline use

The official schema files load their dependencies (other schema files) over HTTP
from OASIS and W3C. This is not optimal if you are using the schema for validating 
files during deployment; it can cause delays while the files are downloaded
and network outages will break your deployment process. 

Editing the schema files to require dependencies from local storage makes the
process much more rapid and reliable.

### X509SerialNumber workaround

Some certificates will trigger this validation error when they are included in
SAML metadata:

```
local-metadata.xml:248: element X509SerialNumber: Schemas validity error : 
Element '{http://www.w3.org/2000/09/xmldsig#}X509SerialNumber': 
'74350910966641747653757015468034054658' is not a valid value of the 
atomic type 'xs:integer'
```
We've followed the advice on resolving this issue from W3C:

> Deployments that expect to make use of the X509IssuerSerial element
> should be aware that many Certificate Authorities issue certificates
> with large, random serial numbers. XML Schema validators may not
> support integer types with decimal data exceeding 18 decimal digits.
> Therefore such deployments should avoid
> schema-validating the X509IssuerSerial element, or make use of a
> local copy of the schema that adjusts the data type of the
> X509SerialNumber child element from "integer" to "string".



## CONTRIBUTORS

* Original files created by OASIS and W3C.
* Changes to dependency locations were made by InCommon.
* Workaround for X509SerialNumber problem by Pete Birkinshaw on behalf of DIL

