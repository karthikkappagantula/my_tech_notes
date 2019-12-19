## Disaster Recovery:
It is all about how to be build systems highly available, fault tolerance, provide good performance and also can recover in the event of a disaster.

* Recovery Point Objective (RPO)
The time between when a disaster occurs and the last recoverable copy of key business data  was created. 

This represents the amount of data you would loose. Minimize the length of this time period through regular backups, snapshots, and transaction logs) to avoid business disruptive data loss.

* Recovery Time Objective (RTO)
The time between when a disaster occurs and when the system can be restored to an operational state and handed over to the business for testing.

Improve this by decreasing the restore time through having spares tested, and ready to use, and enforcing efficient processes.

It is important to understand how each AWS service/product supports RPO/RTO.
