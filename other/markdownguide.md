
# Markwodn Guide



[Heading IDs](#heading-ids)


[Markdown Cheat Sheet](https://www.markdownguide.org/cheat-sheet/)

## Heading {#heading-ids}
# H1
## H2
### H3
#### H4
##### H5
###### H6


## Format

**bold text**

*italicized text*

> blockquote


---

`code`




## Lists

1. First item
2. Second item
    1. 2.1
    2. 2.2
    
    1978\. is year

3. Third item

- First item
- Second item
- Third item

Task List
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

---

## Reference

[title link ](https://www.example.com)

![alt text](image.jpg)

## Table
| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |

## Code Sample

```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```



## Sample API Call
## GET XXX

Retrieve the properties and relationships of a Stock object for Business Central.

### Http Request

Replace the URL endpoint for Dynamics 365 Business Central depending on environment following the [guideline](#endpoints-businesscentralodatav4prefix-structure).

~~~ api
businesscentralodataV4Prefix/XXX
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
{
  "value": [
   
    ]
}
```

### XXX Fields

| Relation | Source Table | Field Caption | Field Type | Field Lenght | Note      |
| ----------- | ----------- | ----------- | ---------- | ------------ |---------- |
|  1          | XXX         | XXX         |  String    | 20           | Primary Key Field SKU Code|
