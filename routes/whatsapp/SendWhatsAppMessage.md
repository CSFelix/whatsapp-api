## Send WhatsApp Message

> General

**- Local Route** - `http://localhost:8080/api/whatsapp/sendMessage/`;

**- Production Route** - `<production_url>/api/whatsapp/sendMessage/`;

**- Method** - `POST`.

---

> Headers

> **Note** - the three headers are required.

**- Content-Type** - must be on `multipart/form-data` format;

**- Authorization** - must be equals to the value of `userApiToken` from `Settings` table in the user database;

**- x-tenant-id** - tenant ID to identify the user;

**- x-connection-api-token** - connection token to identify the whatsapp connection;

**- groupid** - client's group.

---

> Body

> [!NOTE]  
> `phoneNumber` is required and at least one `body` or one `media` is required. `groupId` is only used on production and is not required. `closeTicketSetting` is optional with 1 as default value.

**- phoneNumber** - Contact's WhatsApp Number. Example: `<country_code><ddd><number> - 5518999999999`;

**- body** - text message;

**- medias** - medias messages, such as images, documents, zips, audios and videos;

**- closeTicketSetting** - 1 (tickets are closed after receiving the message) or 0 (tickets are not closed). This option does not work on already created tickets.

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
	"phoneNumber": "5518999999999",
	"body": "Hello World!",
	"medias": "<files>",
 	"closeTicketSetting": "1"
}
```

```json
Response

{
	"status": "200",
	"message": "WhatsApp Message Sent!"
}
```

