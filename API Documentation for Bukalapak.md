# Dokumentasi API VMS dan contoh

### 0.  Retur

#### HTTP Request
```json
localhost:3000/vmsdev/rrn/searchbycdt?page=1&size=5
```
#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| retur_request_number   | required	  	||

#### Result
```json
{
    "code": 0,
    "message": "ok",
    "type": "success",
    "result": [
        {
            "return_request_number": "5218002886",
            "request_created_date": "2018-04-29T05:00:23.900Z",
            "status": "APPROVED",
            "store_code": "019",
            "type": "APPROVED_RQ",
            "read_date": "2018-05-04T03:49:48.882Z",
            "read_by": "0215",
            "action_date": "2018-05-04T03:49:48.687Z",
            "action_by": "0215"
        },
        {
            "return_request_number": "5218002886",
            "request_created_date": "2018-05-02T11:07:31.396Z",
            "status": "NEW",
            "store_code": "104",
            "type": "INCOMING_RQ",
            "read_date": null,
            "read_by": null,
            "action_date": "2018-05-02T11:07:31.396Z",
            "action_by": "SYSTEM"
        },
        {
            "return_request_number": "5218002886",
            "request_created_date": "2018-04-29T05:00:23.900Z",
            "status": "NEW",
            "store_code": "019",
            "type": "INCOMING_RQ",
            "read_date": null,
            "read_by": null,
            "action_date": "2018-04-29T05:00:23.900Z",
            "action_by": "SYSTEM"
        },
        {
            "return_request_number": "5218002886",
            "request_created_date": "2018-04-29T05:00:23.900Z",
            "status": "RQ_AWAITING_ACTION",
            "store_code": "019",
            "type": "INCOMING_RQ",
            "read_date": "2018-05-04T03:44:40.906Z",
            "read_by": "0215",
            "action_date": null,
            "action_by": null
        },
        {
            "return_request_number": "5218002886",
            "request_created_date": "2018-04-25T03:00:25.163Z",
            "status": "NEW",
            "store_code": "029",
            "type": "INCOMING_RQ",
            "read_date": null,
            "read_by": null,
            "action_date": "2018-04-25T03:00:25.163Z",
            "action_by": "SYSTEM"
        }
    ],
    "page": "1",
    "limit": 5
}
```
### 1. Receiving Advice Response

#### HTTP Request
```json
localhost:3000/vmsdev/rar/getRarAll?receiving_advice_number=1115000068
```
#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| receiving_advice_number  | required	  	| 	   |

#### Result

```json
{
    "code": 0,
    "result": {
        "items": [
            {
                "id": "2",
                "purchase_order": "TRI1412233126683",
                "receiving_advice_number": "1115000068",
                "receiving_advice_date": "2023-05-25T00:51:33.915Z",
                "status": "SUPPLIER_DRAFT",
                "po": {
                    "supplier_name": "JKT (RINSO) UNILEVER INDONESIA TBK"
                },
                "store": {
                    "store_id": "428",
                    "name": "Bekasi Harapan"
                }
            },
            {
                "id": "1",
                "purchase_order": "TRI1412233126683",
                "receiving_advice_number": "1115000068",
                "receiving_advice_date": "2023-05-25T00:37:41.408Z",
                "status": "SUPPLIER_DRAFT",
                "po": {
                    "supplier_name": "JKT (RINSO) UNILEVER INDONESIA TBK"
                },
                "store": {
                    "store_id": "428",
                    "name": "Bekasi Harapan"
                }
            },
            {
                "id": "3",
                "purchase_order": "TRI1412233126683",
                "receiving_advice_number": "1115000068",
                "receiving_advice_date": "2023-05-25T00:53:51.896Z",
                "status": "SUPPLIER_DRAFT",
                "po": {
                    "supplier_name": "JKT (RINSO) UNILEVER INDONESIA TBK"
                },
                "store": {
                    "store_id": "428",
                    "name": "Bekasi Harapan"
                }
            },
            {
                "id": "4",
                "purchase_order": "TRI1412233126683",
                "receiving_advice_number": "1115000068",
                "receiving_advice_date": "2023-05-25T18:52:43.807Z",
                "status": "SUPPLIER_DRAFT",
                "po": {
                    "supplier_name": "JKT (RINSO) UNILEVER INDONESIA TBK"
                },
                "store": {
                    "store_id": "428",
                    "name": "Bekasi Harapan"
                }
            }
        ]
    },
    "message": "ok",
    "type": "success"
}
```



### 2. Proforma Invoice Response

#### HTTP Request
```json
localhost:3000/vmsdev/pfir/getPfirAll
```

#### Example

```json
{
    "code": 0,
    "result": {
        "items": [
            {
                "id": "94",
                "revision": "0",
                "date_updated": "2016-01-29T00:06:49.000Z",
                "status": "CANCELLED",
                "ra": {
                    "purchase_order": "TRI1511137638173",
                    "rapo": {
                        "supplier_name": "JKT (SWALLOW) SURYA MAS MENTARI,PT.",
                        "store_code": "038",
                        "delivery_to": "Kramatjati Indah"
                    }
                }
            },
	       },
    "message": "ok",
    "type": "success"
}
```

### 3. Dispatch Advice

#### HTTP Request
```json
localhost:3000/vmsdev/da/getDa?page=1&limit=2&field=status&order=desc
```
#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| page   | required	  	|  	   |
| limit   | required	  	|  	   |
| field  | required	  	|  	   |
| order  | required	  	| 	   |


#### Example
```json
{
    "code": 0,
    "result": {
        "items": [
            {
                "purchase_order": "TRI1603238759565",
                "dispatch_advice_number": "916019159",
                "dispatch_date": "2016-03-24T00:40:19.000Z",
                "status": "SENT",
                "po": {
                    "supplier_name": "JKT (MUNIK) SARI MUNIK",
                    "store_code": "038",
                    "delivery_to": "Kramatjati Indah"
                }
            }
        ]
    },
    "total": 2447,
    "message": "ok",
    "type": "success"
}
```

### 4. Invoice

#### HTTP Request
```json
localhost:3000/vmsdev/i/getInvoiceAll?page=1&size=5&id_invoice=73253620
```
#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| id_invoice   | required	  	|	   |
| page   | required	  	|	   |
| size   | required	  	|	   |

#### Example
```json
{
    "code": 0,
    "result": {
        "items": [
            {
                "purchase_order": "TRI1508246111989",
                "supplier_code": "1639",
                "total_net_amount": 282000,
                "date_updated": "2015-10-01T11:53:03.875Z",
                "status": "PAYMENT_IN_TRANSIT",
                "revision": "0",
                "po": {
                    "po_no": "915061726",
                    "supplier_name": "JKT(KRATIDAENG)ARTA BOGA CEMERLANG",
                    "store_code": "038",
                    "delivery_to": "Kramatjati Indah"
                }
            },
	 },
    "message": "ok",
    "type": "success"
}
```

### 5. Invoice Receipt

#### HTTP Request
```json
localhost:3000/vmsdev/ireceipt/viewbycdt?page=1&size=5
```

#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| page   | required	  	|	   |
| size   | required	  	|	   |

#### Response
```json
{
    "code": 200,
    "message": "ok",
    "type": "succes",
    "result": []
}
```
#5049


### 6. Purchase Order

#### HTTP Request
```json
localhost:3000/vmsdev/po/getPO?page=1&limit=2&field=dept_code&order=desc
```

#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| page   | required	  	|	   |
| limit   | required	  	|	   |
| field   | required	  	|	   |
| order   | required	  	|	   |


#### Response
```json
{
    "code": 0,
    "result": {
        "items": [
            {
                "id": "TRI19090524658093",
                "delivery_to_local": "Kramatjati Indah",
                "status": "PAYMENT_IN_TRANSIT",
                "created_by": "SYSTEM",
                "created_on": "2019-10-29T19:45:56.000Z",
                "last_updated_by": "SYSTEM",
                "last_updated_on": "2020-02-12T21:36:44.000Z",
                "country_code": "ID",
                "currency_order": "IDR",
                "currency_symbol": "Rp",
                "delivery_to": "Kramatjati Indah",
                "dept_code": "FM",
                "department_name": "THEME PARK MERCHANDISE",
                "expected_delivery_date": "2019-11-07T08:00:00.000Z",
                "ext_po_no": "20191029038919031465",
                "order_date": "2019-10-29T12:05:27.000Z",
                "po_no": "919031465",
                "sender_code": "8990380000000",
                "ship_to": "",
                "ship_to_code": "",
                "source_file": "",
                "source_flag": "D",
                "store_code": "038",
                "store_order_number": "",
                "supplier_code": "Y110",
                "suppliereancode": "8993501010011",
                "supplier_fax_number": "",
                "supplier_name": "MITRA PERINTIS MERDEKA PT",
                "supplier_name_local": "MITRA PERINTIS MERDEKA PT",
                "supplier_phone": "021-5279555",
                "total_amount": 100131198,
                "total_quantity": null,
                "mversion": "6",
                "date_updated": "2019-12-10T04:30:00.000Z",
                "supplier_grp_id": null,
                "supplier_department": null,
                "c4bugln": "8990070000000",
                "notification_count": "0",
                "sales_start_date": null,
                "sales_end_date": null,
                "revision_from": "",
                "revision_to": "",
                "business_unit_name": "PT. TRANS RETAIL INDONESIA",
                "business_unit_address": "Jl. Lebak Bulus No. 8 Gedung Carrefour Kebayoran Lama Jakarta Selatan",
                "business_unit_registration": "01.711.062.8-092.000"
            }
        ]
    },
    "total": 217947,
    "message": "ok",
    "type": "success"
}
```
#5049

### 7. Receiving Advice

#### HTTP Request
```json
localhost:3000/vmsdev/ra/getRA?page=1&limit=2&field=dept_code&order=desc
```

#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| page   | required	  	|	   |
| limit   | required	  	|	   |
| field  | required	  	|	   |
| order  | required	  	|	   |


#### Response
```json
{
    "code": 0,
    "result": {
        "items": [
            {
                "id": "23858511",
                "created_by": "SYSTEM",
                "created_on": "2019-11-06T20:12:08.000Z",
                "last_updated_by": "Y110",
                "last_updated_on": "2019-11-27T04:32:57.000Z",
                "mversion": "2",
                "date_updated": null,
                "dept_code": "FM",
                "normal": "Y",
                "receiver_code": "",
                "receiving_advice_date": "2019-11-05T17:00:00.000Z",
                "receiving_advice_number": "1119034792",
                "remarks": "",
                "revision_number": "0",
                "source_file": "",
                "status": "ACCEPTED",
                "store_code": "038",
                "supplier_code": "Y110",
                "supplier_grp_id": null,
                "dispatch_advice": null,
                "purchase_order": "TRI19090524658093",
                "first_approver": "",
                "second_approver": ""
            }
        ]
    },
    "message": "ok",
    "type": "success"
}
```
#5049

### 8. Proforma Invoice

#### HTTP Request
```json
localhost:3000/vmsdev/pfi/getPfiAll?page=1&limit=5&purchase_order=TRI1603288865171
```

#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| page   | required	  	|	   |
| size   | required	  	|	   |
| purchase_order   | required	  	|	   |


#### Response
```json
{
    "code": 0,
    "result": {
        "items": [
            {
                "id": "26",
                "revision": "0",
                "date_updated": null,
                "status": "LITIGATION",
                "purchase_order": "TRI1603288865171",
                "supplier_name": "(LK) SEWU SEGAR NUSANTARA, PT (LOCAL)",
                "store_code": "043",
                "delivery_to": "Carrefour Semarang"
            }
        ]
    },
    "message": "ok",
    "type": "success"
}
```
#5049

### 9. Supplier

#### HTTP Request
```json
localhost:3000/vmsdev/s/userSupplier
```

#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| username   | required	  	|	   |


#### Response
```json
{
    "code": 0,
    "result": [
        {
            "id": "81",
            "username": "0893",
            "email": "ilham_saputra_jati@yopmail.com",
            "enabled": "Y",
            "last_login": "2021-01-19T04:00:58.000Z"
        }
    ],
    "message": "ok",
    "type": "success"
}
```
#5049


