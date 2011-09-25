SAML SCHEMA
==============

## DESCRIPTION
This project contains *slightly* adjusted copies of the SAML protocol schema files 
created and originally published by OASIS.

The files are presented here as a convenience for both DIL and others, especially
as a source for integrating into other projects using Git and Github.

## DERIVATION
The official source of SAML protocol documentation and schemas is here:

  http://docs.oasis-open.org/security/saml/v2.0/
  
This repository is based on InCommon's versions of the official files:

  http://wayf.incommonfederation.org/bridge/docs/

## ADDITIONAL FEATURES
As few as possible - any significant changes to the schema will break compatibility
with the official SAML protocol and cause no end of problems. 

* Schema have been tweaked by InCommon to work when accessed on a local filesystem,
rather than over the Internet. This makes many processes such as verifying SAML metadata
much faster and much more resilient.

 
