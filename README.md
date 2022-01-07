[comment]: # "Auto-generated SOAR connector documentation"
# AWS WAF

Publisher: Splunk Community  
Connector Version: 1\.1\.1  
Product Vendor: AWS  
Product Name: WAF  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.9\.39220  

This app integrates with AWS WAF to add and delete IP addresses

### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a WAF asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**access\_key\_id** |  required  | password | Access Key ID
**access\_key\_secret** |  required  | password | Access Key Secret
**region** |  required  | string | Region

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[add ip](#action-add-ip) - Add a new IP to an existing IP set OR a new IP set  
[delete ip](#action-delete-ip) - Removes IP from an existing IP set  
[list acls](#action-list-acls) - List ACLs  
[list rules](#action-list-rules) - List Rules  
[list ip sets](#action-list-ip-sets) - List IP sets  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'add ip'
Add a new IP to an existing IP set OR a new IP set

Type: **correct**  
Read only: **False**

The ip\_set\_id or ip\_set\_name must be given as input for adding an IP to the IP set, ip\_set\_id will be considered if both ip\_set\_id and ip\_set\_name is provided in input\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**ip\_set\_id** |  optional  | ID of the IP set | string |  `awswaf ip set id` 
**ip\_set\_name** |  optional  | Name of the IP set | string |  `awswaf ip set name` 
**ip\_address** |  required  | IP Address being added | string |  `awswaf ip mask` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.ip\_address | string |  `awswaf ip mask` 
action\_result\.parameter\.ip\_set\_id | string |  `awswaf ip set id` 
action\_result\.parameter\.ip\_set\_name | string |  `awswaf ip set name` 
action\_result\.data\.\*\.ChangeToken | string | 
action\_result\.data\.\*\.IpSetId | string |  `awswaf ip set id` 
action\_result\.data\.\*\.ResponseMetadata\.HTTPHeaders\.content\-length | string | 
action\_result\.data\.\*\.ResponseMetadata\.HTTPHeaders\.content\-type | string | 
action\_result\.data\.\*\.ResponseMetadata\.HTTPHeaders\.date | string | 
action\_result\.data\.\*\.ResponseMetadata\.HTTPHeaders\.x\-amzn\-requestid | string | 
action\_result\.data\.\*\.ResponseMetadata\.HTTPStatusCode | numeric | 
action\_result\.data\.\*\.ResponseMetadata\.RequestId | string | 
action\_result\.data\.\*\.ResponseMetadata\.RetryAttempts | numeric | 
action\_result\.summary\.ip\_status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'delete ip'
Removes IP from an existing IP set

Type: **contain**  
Read only: **False**

The ip\_set\_id or ip\_set\_name must be given as input for adding an IP to the IP set, ip\_set\_id will be considered if both ip\_set\_id and ip\_set\_name is provided in input\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**ip\_set\_id** |  optional  | IP Set ID | string |  `awswaf ip set id` 
**ip\_set\_name** |  optional  | IP Set Name | string |  `awswaf ip set name` 
**ip\_address** |  required  | IP Address | string |  `awswaf ip mask` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.ip\_address | string |  `awswaf ip mask` 
action\_result\.parameter\.ip\_set\_id | string |  `awswaf ip set id` 
action\_result\.parameter\.ip\_set\_name | string |  `awswaf ip set name` 
action\_result\.data\.\*\.ChangeToken | string | 
action\_result\.data\.\*\.ResponseMetadata\.HTTPHeaders\.content\-length | string | 
action\_result\.data\.\*\.ResponseMetadata\.HTTPHeaders\.content\-type | string | 
action\_result\.data\.\*\.ResponseMetadata\.HTTPHeaders\.date | string | 
action\_result\.data\.\*\.ResponseMetadata\.HTTPHeaders\.x\-amzn\-requestid | string | 
action\_result\.data\.\*\.ResponseMetadata\.HTTPStatusCode | numeric | 
action\_result\.data\.\*\.ResponseMetadata\.RequestId | string | 
action\_result\.data\.\*\.ResponseMetadata\.RetryAttempts | numeric | 
action\_result\.summary\.ip\_status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list acls'
List ACLs

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**limit** |  optional  | Maximum number of results \(default\: 100\) | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.limit | numeric | 
action\_result\.data\.\*\.Name | string | 
action\_result\.data\.\*\.WebACLId | string | 
action\_result\.summary\.number\_of\_acls | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list rules'
List Rules

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.data\.\*\.Name | string | 
action\_result\.data\.\*\.RuleId | string | 
action\_result\.summary\.number\_of\_rules | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list ip sets'
List IP sets

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**limit** |  optional  | Maximum number of results \(default\: 100\) | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.limit | numeric | 
action\_result\.data\.\*\.IPSetId | string |  `awswaf ip set id` 
action\_result\.data\.\*\.Name | string |  `awswaf ip set name` 
action\_result\.summary\.number\_of\_ip\_sets | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 