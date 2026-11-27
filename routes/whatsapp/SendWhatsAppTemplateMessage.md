## Send WhatsApp Template Message

> General

> [!NOTE]  
> Only `Official API Connections` are allowed in this route. All requests for Non-Official API Connections will be rejected with HTTP Code `403 (Forbidden)`.
> 

**- Local Route** - `http://localhost:8080/api/whatsappGroup/sendTemplate/`;

**- Production Route** - `<production_url>/api/whatsappGroup/sendTemplate/`;

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
> All properties, but `media`, are required.
>

**- phoneNumber** - Contact's WhatsApp Number. Example: `<country_code><ddd><number> - 5518999999999`;

**- templateUuid** - Meta Template's UUID;

**- media** - a single media. Only `application/pdf`, `image/jpg`, `image/jpeg` and `image/png` up to `5 MB` are allowed;

**- parameters** - Meta Template's parameters.

If template does not contain parameters, the endpoint expects the property `parameters` be set as an empty stringified parameters object. The following snippet shows how to set the property in TypeScript:

```ts
const parameters: MessageTemplateRawParameters = { header: {}, body: {} };

const formData = new FormData();
formData.append('parameters', JSON.stringify(parameters));
```

If template contains parameters, the endpoint expects the property `parameters` be set with a filled stringified parameters object. See the example below in TypeScript:

```ts
const parameters: MessageTemplateRawParameters = {
  header: {
    '<variable_name_or_position>': 'lorem ipsum'
  }

  , body: {
    'variable_name_or_position': 'lorem ipsum'
		, 'another_variable_name_or_position': 'aliud lorem ipsum'
  }
};

const formData = new FormData();
formData.append('parameters', JSON.stringify(parameters));
```

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
  "phoneNumber": "9999999999999",
  "templateUuid": "xxxxxxxx-xxxx-7xxx-xxxx-xxxxxxxxxxxx",
  "media": "<file>",
  "parameters": "{\"header\":{},\"body\":{}}"
}
```

```json
Response

{
  "status": "200",
  "message": "WhatsApp Template Message Sent!"
}
```
