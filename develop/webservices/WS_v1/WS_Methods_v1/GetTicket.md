---
uid: GetTicket
---

# GetTicket

This method is deprecated. <!-- From DataMiner 10.0.13 onwards -->Use the [GetTicketV2](xref:GetTicketV2) method instead.

> [!NOTE]
> DataMiner Ticketing requires a Cassandra database as well as a specific license. <!-- From DataMiner 10.0.13 onwards, -->It also requires an indexing database. For more information on acquiring a Ticketing license, contact the Skyline Sales department.

> [!CAUTION]
>
> - DataMiner Ticketing is being retired. See [DataMiner functionality evolution and retirement](xref:Software_support_life_cycles) for more details. ![EOL](~/dataminer/images/EOL_Duo.png)
> - DataMiner Ticketing is not supported on systems using [Storage as a Service (STaaS)](xref:STaaS).

## Input

| Item           | Format  | Description                                                        |
|----------------|---------|--------------------------------------------------------------------|
| connection     | String  | The connection ID. See [ConnectApp](xref:ConnectApp).              |
| dmaID          | Integer | The ID of the DMA.                                                 |
| ticketID       | Integer | The ID of the ticket.                                              |
| includeHistory | Boolean | Determines whether the revision history of the ticket is included. |

## Output

| Item            | Format                      | Description           |
|-----------------|-----------------------------|-----------------------|
| GetTicketResult | [DMATicket](xref:DMATicket) | The requested ticket. |
