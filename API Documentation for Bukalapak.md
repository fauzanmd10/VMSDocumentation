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

```

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
### 1. Bulk Push

#### HTTP Request
```json
PATCH https://api.bukalapak.com/v2/products/bulk_push.json
```
#### Parameters

| Parameters    |               | Description  |
| ------------- |:-------------:| -------------|
| products_id   | required	  	| `id` dari produk-produk yang ingin dipush (base36) berupa array 	   |
| force         | optional      |   Jika bernilai "1", akan menggunakan saldo BukaDompet jika Paket Push tidak mencukupi untuk melakukan push. Jika bernilai "0", tidak akan menggunakan saldo BukaDompet jika Paket Push tidak mencukupi untuk melakukan push.  	   |

#### Result

| Parameters    |  Description  |
| ------------- |:--------------|
|status| `OK` Jika ada satu/lebih produk yang berhasil di-push. `ERROR` Jika tidak ada produk yang berhasil di-push|
|can_push| Bernilai `true` jika `user` bersangkutan masih dapat melakukan push, dan `false` jika sebaliknya |
|remaining_push| Sisa paket push yang masih tersedia|
|message| Pesan response dari server|
|push_price| Harga untuk melakukan satu kali push|
|deposit| Saldo Bukadompet user|
|success| Array of `id` produk yang berhasil di-push|
|fail| Array of `id` produk yang gagal di-push|

#### Example
```json
curl -u 7:znn36aVeGrtJ2K9Vev6 https://api.bukalapak.com/v2/products/bulk_push.json 
	-X PATCH 
	-d '{"products_id":["s","u","t","a","b","c"], "force":"0"}' 
	-H "Content-Type: application/json"
```
```json
{
	"status":"OK",
	"can_push":true,
	"remaining_push":0,
	"message":"Barang berhasil di-push semuanya",
	"deposit":0,
	"push_price":500,
	"success":["s","u","t","a","b","c"],
	"fail":[]
}
```



### 2. Bulk Set Unavailable

#### HTTP Request
```json
PATCH https://api.bukalapak.com/v2/products/bulk_set_unavailable.json
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
	"status":"OK",
	"message":"Barang berhasil di-set unavailable semuanya",
	"success":["s","u","t","a","b","c"],
	"fail":[]
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
