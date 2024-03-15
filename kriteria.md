# CRITERIA PROJECT

## STRUCTURE OBJECT
```json
{
    id: string,
    title: string,
    createdAt: string,
    updatedAt: string,
    tags: array of string,
    body: string,
}
```
Sample:
```json
{
    id: "note-xkshdkgl",
    title: "History of JavaScript",
    createdAt: "2024-12-23T23:00:09.686Z",
    updatedAt: "2024-12-23T23:00:09.686Z",
    tags: ["NodeJs","JavaScript","Programming"],
    body: "JavaScript pertama kali dikembangkan oleh Brendan Eich dari Netscape di bawah nama Mocha, yang nantinya namanya diganti menjadi LiveScript, dan akhirnya menjadi JavaScript. Navigator sebelumnya telah mendukung Java untuk lebih bisa dimanfaatkan para pemrogram yang non-Java."
}
```

## ADD NOTE
End point
>/notes  

Method/Verbs 
> POST  

Body
```json
{
    "title" : "Judul Catatan",
    "tags": ["tag 1","tag 2"],
    "body": "Isi catatan"
}
```
for id, createdAt and updateAt manage in server-side.
Make sure id should be unique.

response success: status code <b>201(created)</b> 
```json
{
    "status": "success",
    "message": "Catatan berhasil ditambahkan",
    "data": {
        "noteId": "note-xslaksl"
    }
}
```
value of noteId is equal of id.

response failed: status code <b>500</b> 
```json
{
    "status": "error",
    "message": "catatan gagal ditambahkan"
}
```

## VIEW ALL NOTE / LIST NOTE

End point
>/notes  

Method/Verbs
>GET   

response success: status code <b>200(OK)</b> 
```json
{
    "status": "success",
    "data": {
        "notes": [
            {
                "id": "note-ssxljdlsj",
                "title": "judul note",
                "createdAt": "2020-12-23T23:00:09.686Z",
                "updatedAt": "2020-12-23T23:00:09.686Z",
                "tags": ["tag 1", "tag 2"],
                "body": "isi dari catatan 1"
            },
            {
                "id": "note-ssxljdakal",
                "title": "judul note",
                "createdAt": "2020-12-23T23:00:09.686Z",
                "updatedAt": "2020-12-23T23:00:09.686Z",
                "tags": ["tag 1", "tag 2"],
                "body": "isi dari catatan 2"
            }
            {...notes}
        ]
    }
}
```
If there is no data/ note
```json
{
    "status": "success",
    "data": {
        "note": []
    }
}
```
## GET SPECIFIC NOTE 
End point
>/notes/{id}  

Method/Verbs
>GET

response success: status code <b>200(OK)</b>
```json
{
    "status": "success",
    "data": {
        "note": {
            {
                "id": "note-ssxljdlsj",
                "title": "judul note",
                "createdAt": "2020-12-23T23:00:09.686Z",
                "updatedAt": "2020-12-23T23:00:09.686Z",
                "tags": ["tag 1", "tag 2"],
                "body": "isi dari catatan 1"
            }
        }
    }
}
```

response failed: status code <b>404</b>
```json
{
    "status": "error",
    "message": "data not found"
}
```

## UPDATE NOTE
End point
>/notes/{id}  

Method/Verbs
>PUT   

body request: 
```json
{
    "title": "judul catatan revisi",
    "tags": ["tag 1","tag 2"],
    "body": "konten catatan"
}
```

response success: status code <b>200(OK)</b>
```json
{
    "status": "success",
    "message": "catatan berhasil diperbarui"
}
```
If id not found, response failed: status code <b>400</b>
```json
{
    "status": "error",
    "message": "gagal memperbarui catatan, id catatan tidak ditemukan"
}
```

## DELETE NOTE
End point
>/notes/{id}  

Methode/Verbs
>DELETE  

response success; status code <b>200(OK)</b>
```json
{
    "status": "success",
    "message": "catatan berhasil dihapus"
}
```

resonse failde: status code <b>404</b>
```json
{
    "status": "error",
    "message": "catatan gagal dihapus, id tidak ditemukan"
}
```

