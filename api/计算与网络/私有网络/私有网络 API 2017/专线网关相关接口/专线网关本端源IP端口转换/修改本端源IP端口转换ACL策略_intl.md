## 1. API Description

This API (ModifyLocalSourceIPPortTranslationAclRule) is used to modify ACL rules for local IP port translation.
Domain for API request:<font style="color:red">vpc.api.qcloud.com</font>


## 2. Input Parameters
The following request parameter list only provides API request parameters. Common request parameters need to be added when the API is called. For more information, refer to <a href="/doc/api/372/4153" title="Common request parameters">Common Request Parameters</a>. The Action field for this API is ModifyLocalSourceIPPortTranslationAclRule.

| Parameter Name | Required | Type | Description |
|---------|---------|---------|---------|
| vpcId | Yes | String | Virtual private cloud ID assigned by the system, for example: vpc-dfg5445. |
| directConnectGatewayId | Yes | String | Direct Connect gateway ID assigned by the system, for example: dcg-4d545d. |
| translationIPPool | Yes | String | Mapped IP pool. |
| aclRules.n | Yes | Array | ACL rule information. |
| aclRules.n.aclRuleId | Yes | Int | ACL rule ID, for example: 25. |
| aclRules.n.protocol | Yes | String | Protocol: TCP, UDP or ALL. |
| aclRules.n.sourceCidr | Yes | String | The accessed source IP. Support IP and IP segment (CIDR format). If left blank, it refers to all IPs.  |
| aclRules.n.sourcePort | Yes | String | The accessed source port, supporting xx-xx range. If left blank or filled with 0 or 0-0, it means any port is OK.  |
| aclRules.n.destinationCidr | Yes | String | The accessed destination IP, supporting IP and IP segment (CIDR format). If left blank, it refers to all IPs. |
| aclRules.n.destinationPort | Yes | String | The accessed destination port, supporting xx-xx range. If left blank or filled with 0 or 0-0, it means any port is OK. |

## 3. Output Parameters

| Parameter Name | Type | Description |
|---------|---------|---------|
| code | Int | Common error code; 0: Succeeded; other values: Failed. For more information, please refer to <a href="https://intl.cloud.tencent.com/document/product/215/4781" title="Common Error Codes">Common Error Codes</a> on the Error Code page. |
| message | String | Module error message description depending on API. |

 ## 4. Error Code Table
  The following error code list only provides the business logic error codes for this API. For additional common error codes, refer to <a href="https://cloud.tencent.com/doc/api/245/4924" title="VPC Error Codes">VPC Error Codes</a>.
 
| Error Code | Description |
|---------|---------|
| InvalidVpc.NotFound | Invalid VPC. VPC resource does not exist. Please verify that the resource information you entered is correct. This can be queried via the <a href="https://cloud.tencent.com/doc/api/245/%e5%88%9b%e5%bb%ba%e7%a7%81%e6%9c%89%e7%bd%91%e7%bb%9c?viewType=preview" title="Querying Virtual Private Cloud List">Query Virtual Private Cloud List</a> (DescribeVpcEx) API. |
| InvalidDirectConnectGateway.NotFound | Invalid Direct Connect gateway. Direct Connect gateway resource does not exist. Please verify that the resource information you entered is correct. This can be queried via the <a href="https://cloud.tencent.com/doc/api/245/%e6%9f%a5%e8%af%a2%e4%b8%93%e7%ba%bf%e7%bd%91%e5%85%b3?viewType=preview" title="Querying Direct Connect Gateway">Query Direct Connect Gateway</a> (DescribeDirectConnectGateway) API. |
| InvalidLocalSourceIPPortTranslation.NotFound | Invalid local IP port translation rules. Local IP port translation rule does not exist. Please verify that the resource information you entered is correct. |
| InvalidLocalSourceIPPortTranslationAcl.Conflict | ACL rule conflict between local IP port translation rules. The ACL rules for different local IP port translation cannot conflict under the same Direct Connect gateway. |

## 5. Example
Input
<pre>
https://vpc.api.qcloud.com/v2/index.php?Action=ModifyLocalSourceIPPortTranslationAclRule
&<<a href="https://cloud.tencent.com/doc/api/229/6976">Common request parameters</a>>
&vpcId=vpc-dfgg190
&directConnectGatewayId=dcg-ddf14d
&translationIPPool=138.0.0.11-138.0.0.111
&aclRules.0.aclRuleId=26
&aclRules.0.protocol=tcp
&aclRules.0.sourceCidr=111.0.0.1/18
&aclRules.0.sourcePort=80
&aclRules.0.destinationCidr=10.0.0.2/18
&aclRules.0.destinationPort=90
</pre>
Output
```
{
    "code":"0",
    "message":""
}
```


