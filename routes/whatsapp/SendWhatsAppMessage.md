## Send WhatsApp Message

> General

**- Local Route** - `http://localhost:8080/api/whatsapp/sendMessage/`;

**- Production Route** - `<production_url>/api/whatsapp/sendMessage/`;

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
> `phoneNumber` is required and at least one `body` or one `media` is required. `closeTicketSetting` is optional with 1 as default value.

**- phoneNumber** - Contact's WhatsApp Number. Example: `<country_code><ddd><number> - 5518999999999`;

**- body** - text message;

**- medias** - medias messages, such as images, documents, zips, audios and videos. If the connection is using the Meta Official API, only the following medias are allowed:
```json
{
  "AUDIO": {
  "SIZE": "16MB"
    , "EXTENSIONS": [".aac", ".amr", ".mp3", ".m4a", ".ogg"]
  }

  , "DOCUMENT": {
  "SIZE": "100MB"
    , "EXTENSIONS": [".txt", ".csv", ".xls", ".xlsx", ".doc", ".docx", ".ppt", ".pptx", ".pdf", ".zip", ".rar"]
  }

  , "IMAGE": {
  "SIZE": "5MB"
    , "EXTENSIONS": [".jpeg", ".jpg", ".png"]
  }

  , "VIDEO": {
    "SIZE": "16MB"
    , "EXTENSIONS": [".3gp", ".mp4"]
  }
}
```

**- closeTicketSetting** - 1 (tickets are closed after receiving the message) or 0 (tickets are not closed). This option does not work on already created tickets;

**- shouldSkipBlackList** - 1 (dispatch blacklist's validation is not applied and the message is sent regardless whether the contact is into the blacklist or not) or 0 (validation is applied and the message is sent only if the contact is not into the blacklist). If not informed, the value `0` is used as default.

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
 	"closeTicketSetting": "1",
    "shouldSkipBlackList": "0"
}
```

```json
Response

{
	"status": "200",
	"message": "WhatsApp Message Sent!"
}
```






