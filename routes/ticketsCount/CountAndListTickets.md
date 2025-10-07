## CountAndListTickets

> General

**- Local Route** - `http://localhost:8080/api/tickets/countAndList`;

**- Production Route** - `<production_url>/api/tickets/countAndList/`;

**- Method** - `GET`.

---

> Headers

**- Authorization** - must be equals to the value of `userApiToken` from `Settings` table in the user database;

**- x-tenant-id** - tenant ID to identify the user;

**- groupid** - client's group.

---

> Query

**- type (optional)** - Ticket's type. For instance, `0` stands for `Whatsapp Tickets`, `1` for `Note Tickets`, `2` for `Bot Tickets` and `3` for `Internal Chat Tickets`. `[0, 1, 2, 3]` is the default value;

**- status (optional)** - Ticket's status. It can be `[group | channel | open | pending | closed]`. `Pending` is the default value.

---

> Example

```json
Authorization

{
	"Authorization": "<api_key>",
	"x-tenant-id": "1",
	"groupid": "1",
}
```

```json
Query

{
	"type": "0",
	"status": "pending"
}
```

```json
Response

{
	"count": "2",
	"ticketsList": "array[2]"
}
```


