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
#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| products_id   | required	  	| `id` dari produk-produk yang ingin di-set unavailable (base36) berupa array 	   |

#### Result

| Parameters    |  Description  |
| ------------- |:--------------|
|status| `OK` Jika ada satu/lebih produk yang berhasil di-set unavailable. `ERROR` Jika tidak ada produk yang berhasil di-set unavailable|
|message| Pesan response dari server|
|success| Array of `id` produk yang berhasil di-set unavailable|
|fail| Array of `id` produk yang gagal di-set unavailable|


#### Example
```json
curl -u 7:znn36aVeGrtJ2K9Vev6 https://api.bukalapak.com/v2/products/bulk_set_unavailable.json -X PATCH -d '{"products_id":["s","u","t","a","b","c"]}' -H "Content-Type: application/json"
```
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

### 3. Bulk Set Available

#### HTTP Request
```json
PATCH https://api.bukalapak.com/v2/products/bulk_set_available.json
```
#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| products_id   | required	  	| `id` dari produk-produk yang ingin di-set available (base36) berupa array 	   |

#### Result

| Parameters    |  Description  |
| ------------- |:--------------|
|status| `OK` Jika ada satu/lebih produk yang berhasil di-set available. `ERROR` Jika tidak ada produk yang berhasil di-set available|
|message| Pesan response dari server|
|success| Array of `id` produk yang berhasil di-set available|
|fail| Array of `id` produk yang gagal di-set available|

#### Example
```json
curl -u 7:znn36aVeGrtJ2K9Vev6 https://api.bukalapak.com/v2/products/bulk_set_available.json -X PATCH -d '{"products_id":["s","u","t","a","b","c"]}' -H "Content-Type: application/json"
```
```json
{
	"status":"OK",
	"message":"Barang berhasil di-set available semuanya",
	"success":["s","u","t","a","b","c"],
	"fail":[]
}
```

### 4. Bulk Bookmark (Set Favorite)

#### HTTP Request
```json
PATCH https://api.bukalapak.com/v2/favorites/bulk_add.json
```
#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| products_id   | required	  	| `id` dari produk-produk yang ingin di-set favorite (base36) berupa array 	   |

#### Result

| Parameters    |  Description  |
| ------------- |:--------------|
|status| `OK` Jika ada satu/lebih produk yang berhasil di-set favorite. `ERROR` Jika tidak ada produk yang berhasil di-set favorite|
|message| Pesan response dari server|
|success| Array of `id` produk yang berhasil di-set favorite|
|fail| Array of `id` produk yang gagal di-set favorite|


#### Example
```json
curl -u 7:znn36aVeGrtJ2K9Vev6 https://api.bukalapak.com/v2/favorites/bulk_add.json -X POST -d '{"products_id":["s","u","t","a","b","c"]}' -H "Content-Type: application/json"
```
#### Example
```json
{
	"status":"OK",
	"message":"Barang berhasil di-set favorite semuanya",
	"success":["s","u","t","a","b","c"],
	"fail":[]
}
```

### 5. Bulk Unbookmark (Set Unfavorite)

#### HTTP Request
```json
DELETE https://api.bukalapak.com/v2/favorites/bulk_remove.json
```
#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| products_id   | required	  	| `id` dari produk-produk yang ingin di-unset favorite (base36) berupa array 	   |

#### Result

| Parameters    |  Description  |
| ------------- |:--------------|
|status| `OK` Jika ada satu/lebih produk yang berhasil di-unset favorite. `ERROR` Jika tidak ada produk yang berhasil di-unset favorite|
|message| Pesan response dari server|
|success| Array of `id` produk yang berhasil di-unset favorite|
|fail| Array of `id` produk yang gagal di-unset favorite|


#### Request
```json
curl -u 7:znn36aVeGrtJ2K9Vev6 https://api.bukalapak.com/v2/favorites/bulk_remove.json -X DELETE -d '{"products_id":["s","u","t","a","b","c"]}' -H "Content-Type: application/json"
```
#### Response
```json
{
	"status":"OK",
	"message":"Barang berhasil di-unset favorite semuanya",
	"success":["s","u","t","a","b","c"],
	"fail":[]
}
```
#5049
