## Disconnect Sessions

> General

**- Local Route** - `http://localhost:8080/api/session/disconnect`;

**- Production Route** - `<production_url>/api/session/disconnect`;

**- Method** - `PATCH`.

---

> Headers

> [!NOTE]
> `groupId` is only used on production.
>
> `All headers` are required.

**- Authorization** - must be equals to the value of `userApiToken` from `Settings` table in the user database;

**- x-tenant-id** - tenant ID to identify the user;

**- groupid** - client's group.

---

> Body

No request body is required.

---

> Example

```json
Authorization

{
	"Authorization": "<api_key>",
	"x-tenant-id": "1",
	"groupid": "1"
}
```

```json
Response

{
	"status": "200",
	"message": "WhatsApp Sessions Disconnected"
}
```
