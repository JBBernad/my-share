# Bevica Web Integration

## Main Entities

| Name | Description | Data Flow | Operations | Note|
| ----------- | ----------- | ----------- | -------- | ---------- |
| [Customer](#get-customers) | Customer Info and Ship Addresses | BC -> Web | Read | |
| [Product](#get-products) | Items and Attributes | BC -> Web | Read | |
| [Stock](#get-stock) | Stock Available  | BC -> Web | Read | |
| Web Order    | Create Web Order and Lines in BC | Web->BC    | Read Create | |
| Sales Prices | Plain List of Sales Prices| BC -> Web | Read | |
| Payments | Create Payment on Paym. Journal in BC | Web->BC | Create | |
| Manifest | Shipping Manifest Status | BC -> Web | Read | |
| Orders Status | List of Orders with Tracking updates | BC -> Web | Read | |
| SOAP Real Time Functions| Library of function to consume with SOAP Calls | BC -> Web | Read | |

## Endpoints businesscentralodataV4Prefix structure

Common endpoint service

~~~ api
https://api.businesscentral.dynamics.com/<API Version>/<user domain name>/<Enviroment Name>/ODataV4/Company('<Company Namme>')
~~~

Sample

~~~ api
https://api.businesscentral.dynamics.com/v2.0/bevicasaas.onmicrosoft.com/Production/ODataV4/Company('Bevica%20Web%20Integration')
~~~

## GET Customers

Retrieve the properties and relationships of a customer object for Business Central.

### Http Request

Replace the URL endpoint for Dynamics 365 Business Central depending on environment following the [guideline](#endpoints-businesscentralodatav4prefix-structure).

~~~ api
businesscentralodataV4Prefix/WS_Customer_V3
~~~

### Request Headers

Header | Value |
--- | --- |
Authorization | Bearer {token}. Required.|

### Request Body

Do not supply a request body for this method.

### Response

Here is an example of the response

```json
"value": [
        {
            "@odata.etag": "W/\"JzQ0OzMwdHIvR0xYVndidXFwVVBiaGcvS1g0NVFpQWtyNytMYW5ZV2VyVnJxRjg9MTswMDsn\"",
            "No": "1010000",
            "Web_Id": "",
            "Web_Last_Mod_Date_Time": "2022-06-28T15:10:41.603Z",
            "Name": "Asado Bar & Grill",
            "Blocked": " ",
            "Address": "Thatcham Business Village",
            "Address_2": "Colthrop Way",
            "City": "Thatcham",
            "County": "Surrey",
            "Post_Code": "RG19 4LW",
            "Country_Region_Code": "GB",
            "Primary_Contact_No": "CT100292",
            "Contact_Name": "Greg Chapman",
            "Phone_No": "",
            "E_Mail": "greg@contoso.com",
            "Home_Page": "www.Bevica.co.uk",
            "Language_Code": "ENG",
            "Currency_Code": "",
            "Shipment_Method_Code": "EXW",
            "Shipping_Agent_Code": "DHL",
            "Shipping_Agent_Service_Code": "OVERNIGHT",
            "Location_Code": "BLUE",
            "VAT_Registration_No": "",
            "Payment_Terms_Code": "30 DAYS",
            "Payment_Method_Code": "",
            "GLN": "8712345000004",
            "Gen_Bus_Posting_Group": "DOMESTIC",
            "VAT_Bus_Posting_Group": "DOMESTIC",
            "Customer_Posting_Group": "DOMESTIC",
            "Customer_Price_Group": "BARS",
            "Customer_Disc_Group": "",
            "AWRS_URN": "",
            "Territory_Code": "MID",
            "Partner_Type": " ",
            "Privacy_Blocked": false,
            "Salesperson_Code": "ED",
            "Responsibility_Center": "",
            "Global_Dimension_1_Code": "SALES",
            "Global_Dimension_2_Code": "",
            "Balance": 0,
            "Balance_LCY": 0,
            "Balance_Due": 0,
            "Global_Dimension_1_Filter": "",
            "Global_Dimension_2_Filter": "",
            "Currency_Filter": "",
            "Date_Filter": "..06/28/22"
        },
        {
            "@odata.etag": "W/\"JzQ0O0pnMGoxR3pLTTQ1ZFNHME1Gb1BwSUtmc0FKU09ieGxPY0NYSkhJTlpOZ3c9MTswMDsn\"",
            "No": "1020000",
            "Web_Id": "",
            "Web_Last_Mod_Date_Time": "2022-06-28T15:10:41.697Z",
            "Name": "The Pickled Egg Pub",
            "Blocked": " ",
            "Address": "153 Thomas Drive",
            "Address_2": "",
            "City": "",
            "County": "Fife",
            "Post_Code": "KY16 1GY",
            "Country_Region_Code": "GB",
            "Primary_Contact_No": "",
            "Contact_Name": "Mr. Mark McArthur",
            "Phone_No": "",
            "E_Mail": "",
            "Home_Page": "",
            "Language_Code": "ENG",
            "Currency_Code": "",
            "Shipment_Method_Code": "EXW",
            "Shipping_Agent_Code": "DHL",
            "Shipping_Agent_Service_Code": "",
            "Location_Code": "BLUE",
            "VAT_Registration_No": "",
            "Payment_Terms_Code": "14 DAYS",
            "Payment_Method_Code": "",
            "GLN": "8712345000011",
            "Gen_Bus_Posting_Group": "DOMESTIC",
            "VAT_Bus_Posting_Group": "DOMESTIC",
            "Customer_Posting_Group": "DOMESTIC",
            "Customer_Price_Group": "LND GRP",
            "Customer_Disc_Group": "",
            "AWRS_URN": "",
            "Territory_Code": "MID",
            "Partner_Type": " ",
            "Privacy_Blocked": false,
            "Salesperson_Code": "JR",
            "Responsibility_Center": "",
            "Global_Dimension_1_Code": "SALES",
            "Global_Dimension_2_Code": "",
            "Balance": 0,
            "Balance_LCY": 0,
            "Balance_Due": 0,
            "Global_Dimension_1_Filter": "",
            "Global_Dimension_2_Filter": "",
            "Currency_Filter": "",
            "Date_Filter": "..06/28/22"
        }
    ]
}
```

### Customer Fields

| Relation | Source Table | Field Caption | Field Type | Field Lenght | Note |
| ----------- | ----------- | ----------- | -------- | ---------- |---------- |
| 1 | Customer | No. | string | 20 | Primaty Key (Required for Update) |
| 1 | Customer | Web Id | string | 20 | Web Site Id |
| 1 | Customer | Web Last Mod Date Time | datetime |  | Last Update Date Time  |
| 1 | Customer | Name | string | 100 |  |
| 1 | Customer | Name 2 | string | 50 |  |
| 1 | Customer | Blocked | option |  |  |
| 1 | Customer | Address | string | 100 |  |
| 1 | Customer | Address 2 | string | 50 |  |
| 1 | Customer | City | string | 30 |  |
| 1 | Customer | County | string | 30 |  |
| 1 | Customer | Post Code | string | 20 |  |
| 1 | Customer | Country/Region Code | string | 10 |  |
| 1 | Customer | Primary Contact No. | string | 20 |  |
| 1 | Customer | Contact | string | 100 |  |
| 1 | Customer | Phone No. | string | 30 |  |
| 1 | Customer | E-Mail | string | 80 |  |
| 1 | Customer | Home Page | string | 80 |  |
| 1 | Customer | Language Code | string | 10 |  |
| 1 | Customer | Currency Code | string | 10 |  |
| 1 | Customer | Shipment Method Code | string | 10 |  |
| 1 | Customer | Shipping Agent Code | string | 10 |  |
| 1 | Customer | Shipping Agent Service Code | string | 19 |  |
| 1 | Customer | Location Code | string | 10 |  |
| 1 | Customer | VAT Registration No. | string | 20 |  |
| 1 | Customer | Payment Terms Code | string | 10 |  |
| 1 | Customer | Payment Method Code | string | 10 |  |
| 1 | Customer | GLN | string | 13 |  |
| 1 | Customer | Gen. Bus. Posting Group | string | 20 |  |
| 1 | Customer | VAT Bus. Posting Group | string | 20 |  |
| 1 | Customer | Customer Posting Group | string | 20 |  |
| 1 | Customer | Customer Price Group | string | 20 |  |
| 1 | Customer | Customer Disc. Group | string | 20 |  |
| 1 | Customer | AWRS No. | string | 20 |  |
| 1 | Customer | Territory Code | string | 10 |  |
| 1 | Customer | Partner Type | enum |  |  |
| 1 | Customer | Privacy Blocked | bool |  |  |
| 1 | Customer | Salesperson Code | string | 20 |  |
| 1 | Customer | Responsibility Center | string | 10 |  |
| 1 | Customer | Global Dimension 1 Code | string | 20 |  |
| 1 | Customer | Global Dimension 2 Code | string | 20 |  |
| 1 | Customer | Balance | decimal |  |  |
| 1 | Customer | Balance_LCY | decimal |  |  |
| 1 | Customer | Balance Due | decimal |  |  |
| 1..N | Ship-to Address | Customer No. | string | 20 | PK Key (Required for Update) |
| 1..N | Ship-to Address | Code | string | 20 | PK Key (Required for Update)|
| 1..N | Ship-to Address | Name | string | 100 |  |
| 1..N | Ship-to Address | Name 2 | string | 50 |  |
| 1..N | Ship-to Address | Address | string | 100 |  |
| 1..N | Ship-to Address | Address 2 | string | 50 |  |
| 1..N | Ship-to Address | City | string | 30 |  |
| 1..N | Ship-to Address | Contact | string |  |  |
| 1..N | Ship-to Address | Phone No. | string | 100 |  |
| 1..N | Ship-to Address | Shipment Method Code | string | 10 |  |
| 1..N | Ship-to Address | Shipping Agent Code | string | 10 |  |
| 1..N | Ship-to Address | Country/Region Code | string | 10 |  |
| 1..N | Ship-to Address | Post Code | string | 20 |  |
| 1..N | Ship-to Address | County | string | 30 |  |
| 1..N | Ship-to Address | E-Mail | string | 80 |  |
| 1..N | Ship-to Address | Shipping Agent Service Code | string | 10 |  |
| 1..N | Ship-to Address | Service Zone Code | string | 10 |  |
| 1..N | Ship-to Address | Duty Type | string | 10 |  |

## GET Products

Retrieve the properties and relationships of a Item object for Business Central.

### Http Request

Replace the URL endpoint for Dynamics 365 Business Central depending on environment following the [guideline](#endpoints-businesscentralodatav4prefix-structure).

~~~ api
businesscentralodataV4Prefix/WS_Product_V3
~~~

### Request Headers

Header | Value |
--- | --- |
Authorization | Bearer {token}. Required.|

### Request Body

Do not supply a request body for this method.

### Response

Here is an example of the response

```json

"value": [
        {
            "@odata.etag": "W/\"JzQ0O0U5ZXp6Vm9ISEVhakh4QSthNk1MeVhKUU9qZXArMTFVSG5ua0F4ZHZPWDQ9MTswMDsn\"",
            "Code": "B12147",
            "Web_Product_ID": "{73C93262-09B9-464F-9673-2CC0B707DEC4}",
            "Web_Last_Mod_Date_Time": "2022-06-28T15:14:23.827Z",
            "Published": 1,
            "Marketing_Description": "Barolo Riserva DOCG, Vigna Colonello, Marchese Antinori, Prunotto",
            "Category_Code": "STILL RED",
            "Category_Description": "Red Still",
            "Country_Code": "IT",
            "Country_Description": "Italy",
            "Region_Code": "",
            "Region_Description": "",
            "SubRegion_Code": "",
            "SubRegion_Description": "",
            "Producer_Code": "PRUNOTTO",
            "Producer_Name": "Prunotto",
            "Item_Classification": "DOCG",
            "Alcool_Percent": "14%",
            "Vintage": "2010",
            "Grapes": "",
            "Attributes": "Vegan=Yes,Sulphites=Yes",
            "Tags": "IT,,,Yes,Yes,2010,Prunotto,DOCG,14%,Red Still,"
        },
        {
            "@odata.etag": "W/\"JzQ0O3lsQlhaM2xjSU5KaEo4UFZFR3FkdEplRWZieEdWWHdRdGpBMFlJY2xmY0k9MTswMDsn\"",
            "Code": "B12148",
            "Web_Product_ID": "{07119AA4-7F12-484A-ADA1-8F3B82BFCE25}",
            "Web_Last_Mod_Date_Time": "2022-06-28T15:14:32.153Z",
            "Published": 1,
            "Marketing_Description": "Barolo Riserva DOCG, Vigna Colonello, Marchese Antinori, Prunotto",
            "Category_Code": "STILL RED",
            "Category_Description": "Red Still",
            "Country_Code": "IT",
            "Country_Description": "Italy",
            "Region_Code": "",
            "Region_Description": "",
            "SubRegion_Code": "",
            "SubRegion_Description": "",
            "Producer_Code": "PRUNOTTO",
            "Producer_Name": "Prunotto",
            "Item_Classification": "DOCG",
            "Alcool_Percent": "14%",
            "Vintage": "2009",
            "Grapes": "",
            "Attributes": "",
            "Tags": "IT,,,,2009,Prunotto,DOCG,14%,Red Still,"
        },
        {
            "@odata.etag": "W/\"JzQ0O1Naa0dERkxpMW1iQzRERExQTFB3NWRjUFUvMnhRcU94Tng5bjgyNDRDWkk9MTswMDsn\"",
            "Code": "B12154",
            "Web_Product_ID": "{708E3384-FCC5-4AF6-B69B-9E8840573AB5}",
            "Web_Last_Mod_Date_Time": "2022-06-28T15:14:42.053Z",
            "Published": 1,
            "Marketing_Description": "Barolo Riserva DOCG, Vigna Colonello, Marchese Antinori, Prunotto",
            "Category_Code": "STILL RED",
            "Category_Description": "Red Still",
            "Country_Code": "IT",
            "Country_Description": "Italy",
            "Region_Code": "",
            "Region_Description": "",
            "SubRegion_Code": "",
            "SubRegion_Description": "",
            "Producer_Code": "PRUNOTTO",
            "Producer_Name": "Prunotto",
            "Item_Classification": "DOCG",
            "Alcool_Percent": "14%",
            "Vintage": "2012",
            "Grapes": "",
            "Attributes": "",
            "Tags": "IT,,,,2012,Prunotto,DOCG,14%,Red Still,"
        
    ]
}
```

### Product Fields

| Relation | Source Table | Field Caption | Field Type | Field Lenght | Note |
| ----------- | ----------- | ----------- | -------- | ---------- |---------- |
|  1  |  Product  |  Code  |
|  1  |  Product  |  Web Product Id  |
|  1  |  Product  |  Web Last Md. Date Time  |
|  1  |  Product  |  Published  |
|  1  |  Product  |  Last Modification  |
|  1  |  Product  |  Marketing Description  |
|  1  |  Product  |  Category Code  |
|  1  |  Product  |  Category Description  |
|  1  |  Product  |  Country Code  |
|  1  |  Product  |  Country Description  |
|  1  |  Product  |  Region Code  |
|  1  |  Product  |  Region Description  |
|  1  |  Product  |  SubRegion Code  |
|  1  |  Product  |  SubRegion Description  |
|  1  |  Product  |  Producer  |
|  1  |  Product  |  Item Classification  |
|  1  |  Product  |  Alcool Percent  |
|  1  |  Product  |  Vintage  |
|  1  |  Product  |  Grapes  |
|  1  |  Product  |  Attributes  |
|  1  |  Product  |  Tags  |
|  1..1    |  SKU\Variant  |  Web Item Id  |
|  1..1    |  SKU\Variant  |  Published  |
|  1..1    |  SKU\Variant  |  Deleted  |
|  1..1    |  SKU\Variant  |  Web Last Mod. Date Time  |
|  1..1    |  SKU\Variant  |  Item No  |
|  1..1    |  SKU\Variant  |  Blocked  |
|  1..1    |  SKU\Variant  |  Last Modification  |
|  1..1    |  SKU\Variant  |  Description  |
|  1..1    |  SKU\Variant  |  Base UoM Code  |
|  1..1    |  SKU\Variant  |  Base UoM Description  |
|  1..1    |  SKU\Variant  |  Sales UoM Code  |
|  1..1    |  SKU\Variant  |  Sales UoM Description  |
|  1..1    |  SKU\Variant  |  Sales UoM Qty Per  |
|  1..1    |  SKU\Variant  |  Unit Volume  |
|  1..1    |  SKU\Variant  |  Unit Price With Duty  |
|  1..1    |  SKU\Variant  |  Unit Price WithOut Duty  |
|  1..1    |  SKU\Variant  |  Stock Quantity Base  |
|  1..1    |  SKU\Variant  |  Bottle   |
|  1..1    |  SKU\Variant  |  Sell Case Only  |



## GET Stock

Retrieve the properties and relationships of a Stock object for Business Central.

### Http Request

Replace the URL endpoint for Dynamics 365 Business Central depending on environment following the [guideline](#endpoints-businesscentralodatav4prefix-structure).

~~~ api
businesscentralodataV4Prefix/WS_Stock_V3
~~~

### Request Headers

Header | Value |
--- | --- |
Authorization | Bearer {token}. Required.|

### Request Body

Do not supply a request body for this method.

### Response

Here is an example of the response

```json

"value": [
        {
            "@odata.etag": "W/\"JzQ0OzZuUmRLaHlpY1lIbkcxVWEvaGxDOW1tdzdaR2dLdVp3d2J4S1g4NGU1UHc9MTswMDsn\"",
            "Group_Code": "",
            "Item_No": "B12147",
            "Variant_Code": "",
            "Unit_of_Measure_Code": "75CL",
            "Location_Code": "BLUE",
            "Qty_per_Unit_of_Measure": 1,
            "Stock_Available_Base": 1320,
            "Last_Mod_Date_Time": "2022-06-28T16:01:26.077Z"
        },
        {
            "@odata.etag": "W/\"JzQ0OzNwbWNwTHlmOURUSHhkWFpTK1VGTWVzVExiNlpDRS9rVzExdSt0YVMwSlU9MTswMDsn\"",
            "Group_Code": "",
            "Item_No": "B12148",
            "Variant_Code": "",
            "Unit_of_Measure_Code": "75CL",
            "Location_Code": "BLUE",
            "Qty_per_Unit_of_Measure": 1,
            "Stock_Available_Base": 0,
            "Last_Mod_Date_Time": "2022-06-28T16:01:26.107Z"
        },
        {
            "@odata.etag": "W/\"JzQ0O1U0b1dOb25wQnFWUkFWNXBkbXEvVDZBQnhRRldNeFBSeXMzNmUvOGh5WGc9MTswMDsn\"",
            "Group_Code": "",
            "Item_No": "B12154",
            "Variant_Code": "",
            "Unit_of_Measure_Code": "75CL",
            "Location_Code": "BLUE",
            "Qty_per_Unit_of_Measure": 1,
            "Stock_Available_Base": 6000,
            "Last_Mod_Date_Time": "2022-06-28T16:01:26.12Z"
        },
        {
            "@odata.etag": "W/\"JzQ0O0t1SEFTQzFPUXRmaXpxL0RNMHUxeTVxZFlxcXczdmZnUU5RU3BYV3hQVTg9MTswMDsn\"",
            "Group_Code": "",
            "Item_No": "B12161",
            "Variant_Code": "",
            "Unit_of_Measure_Code": "37.5CL",
            "Location_Code": "BLUE",
            "Qty_per_Unit_of_Measure": 1,
            "Stock_Available_Base": 0,
            "Last_Mod_Date_Time": "2022-06-28T16:01:26.137Z"
        },
        {
            "@odata.etag": "W/\"JzQ0O3ZwSzErUG1BRmRiZFJ0amZyU3llWUlvUEUvM1VXQnU4eVdibTg5TUZLRjg9MTswMDsn\"",
            "Group_Code": "",
            "Item_No": "B12168",
            "Variant_Code": "",
            "Unit_of_Measure_Code": "37.5CL",
            "Location_Code": "BLUE",
            "Qty_per_Unit_of_Measure": 1,
            "Stock_Available_Base": 0,
            "Last_Mod_Date_Time": "2022-06-28T16:01:26.153Z"
        },
        {
            "@odata.etag": "W/\"JzQ0O0dCbVViY1dOSStUMDlIMi9PdmY0YStuWnJ2RHNHaHEvMnNJVENpRVpYeUk9MTswMDsn\"",
            "Group_Code": "",
            "Item_No": "B62470",
            "Variant_Code": "",
            "Unit_of_Measure_Code": "75CL",
            "Location_Code": "BLUE",
            "Qty_per_Unit_of_Measure": 1,
            "Stock_Available_Base": 0,
            "Last_Mod_Date_Time": "2022-06-28T16:01:26.153Z"
        }
    ]
}
```

### Stock Fields

| Relation | Source Table | Field Caption | Field Type | Field Lenght | Note |
| ----------- | ----------- | ----------- | -------- | ---------- |---------- |
|  1  |  Group_Code  |  String  |
|  1  |  Item_No  |  String  |
|  1  |  Variant_Code  |  String  |
|  1  |  Unit_of_Measure_Code  |  String  |
|  1  |  Location_Code  |  String  |
|  1  |  Qty_per_Unit_of_Measure  |  Decimal  |
|  1  |  Stock_Available_Base  |  Decimal  |
|  1  |  Last_Mod_Date_Time  |  Date Time  |

### Recommended Content

[Business Central Standard Web Service ](BC/Readme.md)
