## Send WhatsApp Group Message

> General

**- Local Route** - `http://localhost:8080/api/whatsappGroup/sendMessage/`;

**- Production Route** - `<production_url>/api/whatsappGroup/sendMessage/`;

**- Method** - `POST`.

---

> Headers

> [!NOTE]  
> `groupId` is only used on production.
> 
> `All headers` are required.

**- Content-Type** - must be on `multipart/form-data` format;

**- Authorization** - must be equals to the value of `userApiToken` from `Settings` table in the user database;

**- x-tenant-id** - tenant ID to identify the user;

**- x-connection-api-token** - connection token to identify the whatsapp connection;

**- groupid** - client's group.

---

> Body

> [!NOTE]  
> `jid` is required and at least one `body` or one `media` is required.

**- jid** - Group's WhatsApp JID;

**- body** - text message;

**- medias** - medias messages, such as images, documents, zips, audios and videos.

---

> Example

```json
Authorization

{
	"Content-Type": "multipart/form-data",
	"Authorization": "<api_key>",
	"x-tenant-id": "1",
	"x-connection-api-token": "<connection_api_key>",
	"groupid": "1"
}
```

```json
Body

{
	"jid": "999999999999999999",
	"body": "Hello World!",
	"medias": "<files>"
}
```

```json
Response

{
	"status": "200",
	"message": "WhatsApp Group Message Sent!"
}
```
