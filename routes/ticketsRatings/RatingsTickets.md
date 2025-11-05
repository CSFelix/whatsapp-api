## RatingsTickets

> General

**- Local Route** - `http://localhost:8080/api/tickets/ratings`;

**- Production Route** - `<production_url>/api/tickets/ratings`;

**- Method** - `GET`.

---

> Headers

**- Authorization** - must be equals to the value of `userApiToken` from `Settings` table in the user database;

**- x-tenant-id** - tenant ID to identify the user;

**- groupid** - client's group.

---

> Query

**- timestamp** - timestamp to filter tickets. All tickets with property `updatedAt` greater than or equals to the parameter will be fetched.

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
Query

{
	"timestamp": "10800000"
}
```

```json
Response

{
	"tickets": "array[]"
}
```