<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [AWS Security](#aws-security)
  - [Security](#security)
  - [data](#data)
  - [Encryption](#encryption)
  - [Some customers feedback](#some-customers-feedback)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# AWS Security
    Steven Schmidt, Amazon head of Security

## Security
We have to look at security from different perspectives to understand it all: CTO, CEO, PR.

Security is Amazon number one priority.

Security covers several aspects:
* physical
* network
* platforms
* people and procedures

Tom Dodustorm, NASA JPL CTO, says that "AWS is more secure than their own datacenters"

Security is here to provide
* more **visibility**
    * trusted advisor
    * APIs
* more **auditability**
    * audits made by 3rd party auditors
    * received many awards and certifications: ISO, PCI DSS...
* more **control**
    * fine grained ACLs
    * never depend on *one* security control

AWS CloudTrail records every API call. This can be logged to analyse, protect (with IAM) and archive.

AWS Staff access: *least priviledge principle*
* staff vetting (background check is run on recruitment)
* no logical access to customer instances
* very limited access. accesses are controled and monitored
* different badges to enter data center
* no HD may leave a data center intact: everything is destroyed

## data
You can define what system has access to other system. For instance, you can prevent the webserver from accessing the database.

Data stays in the region and the availability zone where you put it. No data is moved between regions.

AWS is:
* 10 regions
* 26 availability zones
* 51 edge locations

## Encryption
It can be
* automated (all is made by AWS)
* enabled
* on client side

AWS Cloud HSM (Hardware Security Module): Amazon can't access to the keys, not event the governments.

## Some customers feedback
* Axway
