# rhvm_ipa_auth
# Configure RHV Manager for IdM kerberos authentication.

Ansible integration was based on Documenation provided in the Administration Guide for 4.1 chapter 16 and Appendix D

There are roles to put the engine into and out of maintenance mode and a rhvm_ipa_auth role that does the following:

- ensures proper repos are enabled
- install IdM client and RHV authentication packages on the systems and updates
- unregisters and reregisters the rhvm system from IdM
- creates a service principal
- retrieves the keytab
- creates private, public keys, csr and generates an IPA signed cert
- ensures subjectAltName is properly set to DNS name
- configures rhvm SSL to use the new cert
- configures rhvm to use IPA a authentication source
- restarts services appropriately

##NOTES:
- these roles are not extensively "variablized" to reduce the required configuration as they are intended for a specific purpose
- variables for the rhvm_ipa_auth role are located under group_vars - examples are provided complete documentation will follow.
- the lab_builder project will eventually house this set of roles.
- lab_builder contains the ansible roles to build an IdM server and add basic users for RHVM (I think I added users, if not I will???)
- this will be expanded when RHV 4.2 comes out to include the ansible roles to configure each RHVH server for IdM certificates and IdM central login for SSH and Cockpit

Pull requests are welcome

###Tested with:
ipa --version
VERSION: 4.5.0, API_VERSION: 2.228

rpm -qa ovirt-engine
ovirt-engine-4.1.3.5-0.1.el7.noarch
