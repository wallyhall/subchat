# subchat
Simple messaging protocol for IP subnets.

This messaging protocol (and associated implementations) was born out of the desire for simple, robust and cost-effective mechanism to announce events across local networks.

Such examples include Zabbix and Jenkins - for which an early escalation step for alerts may be appropriately solutioned without resorting to something complex and expensive like SMS.

`subchat` is an abstract and simple (and fairly minimal) protocol for delivering messages on an IP subnet.

Two "super" classifications of actors are defined:

 - **Residents** ("resident senders"): a message sender who is under the direct administrative control of the network administrators.  For example, a Zabbix installation.
 - **Visitors**: message sender/recipients who are not neccessarily under the direct administrative control of the network administrators.  For example, BYOD mobile devices and employee laptops etc.

"Visitors" are further divided into two "sub" classifications, which are relevant from the perspective of one visitor to another:

 - **Strangers**
 - **Acquaintances**

All visitors are by default "strangers" to one another unless a mutual public/private key exchange has occurred - upgrading them to "acquaintance" status.

Messages are classified as one of three:

 - **Public broadcasts**: a message is broadcasted on the subnet and any all visitors may choose to listen
 - **Private broadcasts**: as public, but encrypted (and signed) with a pre-shared key
 - **Unicast**: a message sent directly from one peer to another

Security is not a paramount feature.  If strong encryption and proof of authenticity is required, `subchat` is not a valid solution.  Other technologies such as TLS and RSA exist for that.

`subchat` includes a very basic **optional** provisioning for encryption and proof of authenticity - but only for the sake of making the protocol less open to abuse where uncontrolled devices may be present (such as BYOD environments).  These provisions do not make the protocol *secure*.
