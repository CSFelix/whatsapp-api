## Send Annotation Message

> General

**- Local Route** - `http://localhost:8080/api/annotation/sendMessage/`;

**- Production Route** - `<production_url>/api/annotation/sendMessage`;

**- Method** - `POST`.

---

> Headers

> **Note** - the three headers are required.

**- Content-Type** - must be on `multipart/form-data` format;

**- Authorization** - must be equals to the value of `userApiToken` from `Settings` table in the user database;

**- x-tenant-id** - tenant ID to identify the user.

---

> Body

> [!NOTE]  
> `noteName` is required and at least one `body` or one `media` is required. `GroupId` is only used on production and is not required.

**- noteName** - alias for the note;

**- body** - text message;

**- medias** - medias messages, such as images, documents, zips, audios and videos;

**- groupId** - vps to send the message.

---

> Example

```json
Headers

{
	"Content-Type": "multipart/form-data",
	"Authorization": "<api_key>",
	"x-tenant-id": "1"
}
```

```json
Body

{
	"noteName": "FX Sistemas",
	"body": "Hello World!",
	"medias": "<files>",
	"groupdId": "1",
}
```

```json
Response

{
	"status": "200",
	"message": "Annotation Message Sent!"
}
```
