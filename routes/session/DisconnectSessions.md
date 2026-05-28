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

**- x-api-application-token** - check with developers;

**- x-target-tenant-id** - tenant ID that all sessions will be disconnected;

**- x-tenant-id** - tenant ID from the requisition to identify the user;

**- groupid** - client's group.

---

> Body

No request body is required.

---

> Example

```json
Authorization

{
	"x-api-application-token": "<api_application_key>",
	"x-tenant-id": "1",
    "x-target-tenant-id": "2",
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
