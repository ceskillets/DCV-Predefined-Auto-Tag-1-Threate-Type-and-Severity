
# **Predefined Log-Filter of threat type and severity with Auto-Tag for stepwise security policies**  

<img src="https://github.com/HidetoKusakawa/StepwisePolicy1/blob/master/Stepwise_policy1/Images/Loupe.jpg">    


------------------------------------------------------------------------------------------------------------


## *Brief Description*  
This is a skillet configuring predefined auto tag filter to adjust the security policy on the endpoint’s log.  
## *Target Audience*  
SEs and Partners  
## *Skillet Details*  
Authoring Group:  Datacenter Virtualization  
Documentation:  Docouments about Auto-tag and log forwarding  
[PAN-OS configuration guide about auto tag](https://docs.paloaltonetworks.com/pan-os/9-0/pan-os-admin/monitoring/configure-log-forwarding.html)

Github Location:  https://
PAN-OS Supported:  tested version is PAN-OS 9.0  
Cloud Provider(s) Supported:  any Cloud Provider is supported as well as on-premises DCs  
Type of Skillet:  One xml  
Purpose:  Demo  
Status:  draft  

### Detail Description  
This skillet is for SE and Partners and to use a demonstration for customers to understand our auto tag feature. Particularly, in the case that a Datacenter customer wants a NGFW to adjust or tune automatically the security policy/rule with reaction to the endpoint behavior, in order to reduce their maintenance works with huge amount of logs.  

 Auto-tag feature can add a tag in source IP address or destination IP address  filtered using log forwarding’s action with user-defined filter. Particularly, in datacenter use-case it is risky for the customer to take deny action of the servers soon and due to the fact that there would be huge amount of logs, the customer could not investigate to step it to the more strict policy.   
 Automatic stepwise policy would be helpful for  the customer, however it is not easy for some customers to define the filter which endpoints traffic should be raised to next strict policy.  
 This skillet helps the customer deploy the filter easier and helps SEs and Partner provide predefined filters with the customer.  

### How does the skillet works.  
Configure a Tag  
Configure a Dynamic IP address list  
Configure a Log forwarding with some filter and an action adding the Tag with pre-defined filter  
Configure a sampled base-line security policy with the Log warding  
Configure a strict security policy for tagged ip address.  

<img src="https://github.com/HidetoKusakawa/StepwisePolicy1/blob/master/Stepwise_policy1/Images/fugire1.jpg">  

### Variable:  
Tag name, Tag color, Dynamic IP list name,log forwarding name, filter name….  

### Predefined filter:  
~~~~
  Type: threat
~~~~

~~~~
  Filter: ((threat-type eq vulnerability) or (threat-type eq scan) or (threat-type eq wildfire-virus) or (threat-type eq spyware) or (threat-type eq attack)) and (severity geq medium)
  Target: Destination
~~~~

### Strict Policy:
~~~~
  Source Tagged ip address　-> any with strict profile
~~~~
  
  

<img src="https://github.com/HidetoKusakawa/StepwisePolicy1/blob/master/Stepwise_policy1/Images/fugire2.jpg">


<img src="https://github.com/HidetoKusakawa/StepwisePolicy1/blob/master/Stepwise_policy1/Images/fugire3.jpg">  



# Support Policy  
The code and templates in the repo are released under an as-is, best effort, support policy. These scripts should be seen as community supported and Palo Alto Networks will contribute our expertise as and when possible. We do not provide technical support or help in using or troubleshooting the components of the project through our normal support options such as Palo Alto Networks support teams, or ASC (Authorized Support Centers) partners and backline support options. The underlying product used (the VM-Series firewall) by the scripts or templates are still supported, but the support is only for the product functionality and not for help in deploying or using the template or script itself. Unless explicitly tagged, all projects or work posted in our GitHub repository (at https://github.com/PaloAltoNetworks) or sites other than our official Downloads page on https://support.paloaltonetworks.com are provided under the best effort policy.  

