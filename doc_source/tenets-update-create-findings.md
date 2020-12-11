# Tenets for creating and updating findings<a name="tenets-update-create-findings"></a>

As you plan how you will create and update findings in AWS Security Hub, keep the following tenets in mind\.

**Make findings specific so that customers can easily take action on them\.**  
Customers want to automate response and remediation actions and correlate findings with other findings\. To support this, findings should have the following characteristics:  
+ They should generally deal with a single or primary resource\.
+ They should have a single finding type\.
+ They should deal with a single security event\.
When a finding contains data for multiple security events, it is more difficult for customers to take action on the finding\. 

**Map all of your finding fields to the AWS Security Finding Format \(ASFF\)\. Allow customers to rely on Security Hub as a source of truth\.**  
Customers expect that every field that is in your native finding format is also represented in the Security Hub ASFF\.  
Customers want all data to be present in the Security Hub version of the finding\. Missing data causes them to lose trust in Security Hub as a central source of security information\. 

**Minimize redundancy in findings\. Do not overwhelm customers with finding volumes\.**  
Security Hub is not a general log management tool\. You should send findings to Security Hub that are highly actionable, and that customers can directly respond to, remediate, or correlate with other findings\.  
When there is only a minor change to the finding, update the finding instead of creating a new finding\.  
When there is a major change to the finding, such as to the severity score or resource identifier, create a new finding\.  
For example, to create findings for individual port scans in real time is not highly actionable\. Because port scanning can happen continuously, it would produce a large volume of findings\. It is far more compelling and precise to simply update the last scan time and scan count on a single finding for a port scan on a MongoDB port from a TOR node\.

**Allow customers to customize their findings to make them more meaningful\.**  
Customers want to be able to adjust certain finding fields to make them more relevant to their environment or requirements\.  
For example, customers want to be able to add notes, tags, and adjust severity scores based on the type of account or the type of resource that the finding is associated with\.