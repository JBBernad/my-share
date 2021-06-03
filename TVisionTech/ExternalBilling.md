# TVision External Billing API Specificaiton


## Business Central API Overview

[Endpoints for the APIs for Dynamics 365 Business Central On-Premises and Online](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/api-reference/v2.0/endpoints-apis-for-dynamics)

[Operational Limits for Business Central API V2.0](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/api-reference/v2.0/dynamics-rate-limits)

[Get Company Id](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/api-reference/v2.0/api/dynamics_company_get)

## Endpoints

```code
https://api.businesscentral.dynamics.com/{{BCAPIVersion}}/{{endpoint}}/api/{{APIPublisher}}/tvtExternalBilling/{{APIVersion}}/
```

{{BCAPIVersion}} = 'v2.0'

{{APIPublisher}} = 'tvisiontech'

{{APIVersion}} ='v1.0'

{{endpoint}} := 'bevicabc.onmicrosoft.com/Sandbox' (replace with your domain name)

### Http Request

Replace the URL endpoint for Dynamics 365 Business Central depending on environment following the [guideline](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/api-reference/v2.0/endpoints-apis-for-dynamics).


~~~api
GET https://api.businesscentral.dynamics.com/v2.0/bevicabc.onmicrosoft.com/Sandbox/api/tvisiontech/tvtExternalBilling/v1.0/
~~~

### Request Header

Header | Value |
--- | --- |
Authorization | Bearer {token}. Required.|


### Response Body

If successful, this method returns 201 Created response code and a salesTransactions object in the response body.

### Example

Response

Here is an example of a response.

```json
{
    "@odata.context": "https://api.businesscentral.dynamics.com/v2.0/bevicabc.onmicrosoft.com/Sandbox/api/tvisiontech/tvtExternalBilling/v1.0/$metadata",
    "value": [
        {
            "name": "entityDefinitions",
            "kind": "EntitySet",
            "url": "entityDefinitions"
        },
        {
            "name": "companies",
            "kind": "EntitySet",
            "url": "companies"
        },
        {
            "name": "subscriptions",
            "kind": "EntitySet",
            "url": "subscriptions"
        },
        {
            "name": "salesTransactions",
            "kind": "EntitySet",
            "url": "salesTransactions"
        },
        {
            "name": "bulkPost",
            "kind": "EntitySet",
            "url": "bulkPost"
        },
        {
            "name": "purchaseTransactions",
            "kind": "EntitySet",
            "url": "purchaseTransactions"
        }
    ]
}
```


## Sales Transactions

Create a sale transaction entry in Dynamics 365 Busines Central


Field Name | Description | Note
--- | --- |--- |
transactionGroupCode | A unique code to identify the type of transaction be created within BC using the other setup fields| Mandatory Code 20 |
documentNo | Business Central Document No. Grouping Code for lines| Mandatory Code 20 |
externalDocumentNo | External Document No.| Code 35 |
documentLineNo | Line No. | Mandatory Integer |
customerNo | Business Central Customer No.| Mandatory Code 20|
documentDate | Document Date |  |
lineType | Specifies the type of transaction that will be posted with the document line.Values: G/L Account; Item; Resource| Mandatory Enum |
no | G/L Account No. Or Item No. Or Resource No. | Mandatory Code 20|
quantity | Quantity | Decimal |
description | Specifies a description of the entry of the product to be sold. To add a non-transactional text line, fill in the Description field only.| Text 100 |
unitPrice | Specifies the price for one unit on the sales line| |
vatProdPostGroup | Specifies the VAT specification of the involved item or resource to link transactions made for this record with the appropriate general ledger account according to the VAT posting setup|  |
dim1 | Dimension Value 1 for the current transaction.|  |
dim2 | Dimension Value 2 for the current transaction.|  |
dim3 | Dimension Value 3 for the current transaction.|  |
dim4 | Dimension Value 4 for the current transaction.|  |
dim5 | Dimension Value 5 for the current transaction.|  |
dim6 | Dimension Value 5 for the current transaction.|  |
dim7 | Dimension Value 5 for the current transaction.|  |
dim8 | Dimension Value 5 for the current transaction.|  |



### Http Request

Replace the URL endpoint for Dynamics 365 Business Central depending on environment following the [guideline](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/api-reference/v2.0/endpoints-apis-for-dynamics).

~~~ api
https://api.businesscentral.dynamics.com/v2.0/{{endpoint}}/api/tvisionTech/tvtExternalBilling/v1.0/companies({{Companyid}})/salesTransactions
~~~

### Request Header

Header | Value |
--- | --- |
Authorization | Bearer {token}. Required.|

### Request Body

In the request body, supply a JSON representation of a salesTransactions object.

### Response Body

If successful, this method returns 201 Created response code and a salesTransactions object in the response body.

### Example

Request

Here is an example of a request.

~~~
POST https://api.businesscentral.dynamics.com/v2.0/{{endpoint}}/api/tvisionTech/tvtExternalBilling/v1.0/companies({{Companyid}})/salesTransactions

Content-type: application/json
~~~

```json
{
    "transactionGroupCode": "SINVOICE",
    "documentNo": "SI21-010101",
    "externalDocumentNo" : "Ext. Sales Inv. 8",
    "documentLineNo": "10000",
    "customerNo": "30000",
    "documentDate": "2020-06-13",
    "lineType": "G/L Account",
    "no": "10100",
    "description": "Line Description",
    "quantity": 1,
    "vatProdPostingGroup" : "FULL20",
    "unitPrice": 222,
    "dim1" :"SALES"
}
```



## Post Bulk

Create a multiple transaction entries in Dynamics 365 Busines Central

### Http Request

Replace the URL endpoint for Dynamics 365 Business Central depending on environment following the [guideline](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/api-reference/v2.0/endpoints-apis-for-dynamics).

~~~ api
https://api.businesscentral.dynamics.com/v2.0/{{endpoint}}/api/tvisionTech/tvtExternalBilling/v1.0/companies({{Companyid}})/bulkPost?$expand=salesTransactions
~~~

### Request Header

Header | Value |
--- | --- |
Authorization | Bearer {token}. Required.|

### Request Body

In the request body, supply a JSON representation of an array of  salesTransactions objects.

### Response Body

If successful, this method returns 201 Created response code and a salesTransactions object in the response body.

### Example

Request

Here is an example of a request.

~~~
POST https://api.businesscentral.dynamics.com/v2.0/{{endpoint}}/api/tvisionTech/tvtExternalBilling/v1.0/companies({{Companyid}})//bulkPost?$expand=salesTransactions

Content-type: application/json
~~~

```json
{
    "salesTransactions": 
        [
            {
            "transactionGroupCode": "SINVOICE",
            "documentNo": "SI21-010101",
            "externalDocumentNo" : "Ext. Sales Invoice 8",
            "documentLineNo": "10000",
            "customerNo": "30000",
            "documentDate": "2020-06-13",
            "lineType": "G/L Account",
            "no": "10100",
            "description": "Line Description",
            "quantity": 1,
            "vatProdPostingGroup" : "STANDARD",
            "unitPrice": 222,
            "dim1" :"SALES"}
            ,
			{
            "transactionGroupCode": "SINVOICE",
            "documentNo": "SI21-010101",
            "externalDocumentNo" : "Ext. Sales Invoice 8",
            "documentLineNo": "20000",
            "customerNo": "30000",
            "documentDate": "2020-06-13",
            "lineType": "G/L Account",
            "no": "10100",
            "description": "Line Description",
            "quantity": 1,
            "vatProdPostingGroup" : "STANDARD",
            "unitPrice": 222,
            "dim1" :"SALES"
            }
        ]
}
```


