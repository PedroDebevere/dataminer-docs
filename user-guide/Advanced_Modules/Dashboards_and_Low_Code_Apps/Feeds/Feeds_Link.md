---
uid: Feed_Link
---

# Dynamically referencing data in text

From DataMiner 10.3.11/10.4.0 onwards<!-- RN 37229 -->, some Dashboards and Low-Code Apps features allow you to link to data by dynamically referencing data values from the dashboard or low-code app in specific text fields.

> [!TIP]
> You can for example use this to [navigate to a URL](xref:LowCodeApps_event_config#navigating-to-a-url) that is dynamically adjusted based on a data value.

> [!NOTE]
> To know whether a specific Dashboards or Low-Code Apps feature supports this syntax, refer to the documentation for this feature.

## Feeds

### Syntax

To create feed references inside textual settings, use the following syntax:

```txt
{FEED.Source name.Feed name.Category name.Data type.Property name}
```

- **FEED**: A fixed keyword to indicate that the variable represents a feed link.

- **Source name**: The name of the low-code app page or panel, e.g. "Page 1".

  > [!NOTE]
  > When you link a feed to a [Web](xref:DashboardWeb) or [Text](xref:DashboardText) component in a dashboard, omit the source name.<!--RN 38993-->

- **Feed name**: The name of the feed, e.g. "Table 3".

- **Category name**: The part of the feed that will contain the data, e.g. "Selected rows".

- **Data type**: The type of data, e.g. "Elements".

- **Property name**: The property of the fed data that should be used, e.g. "Protocol Name".

> [!TIP]
> You can find the name of each part in the *FEEDS* data source of the edit panel's *DATA* tab.

> [!NOTE]
>
> - Any parts of this syntax that contain spaces should be enclosed in double quotation marks.
> - All parts of this syntax are case-sensitive.

### Example

If the linked feed provided the element name "Localhost" and the protocol name "Microsoft Platform", the following example would result in the text "*The element Localhost uses the protocol Microsoft Platform*":

```txt
The element `{FEED."Page 1"."Dropdown 3"."Selected item".Elements.Name}` uses the protocol `{FEED."Page 1"."Dropdown 3"."Selected item".Elements."Protocol Name"}`.
```

## Flows

Flows are available starting from DataMiner web 10.4.12. The minimum required server version is 10.4.0 or 10.3.9.

> [!TIP]
> See also: [Flows](xref:Using_flows)

### Syntax

To create a flow reference inside textual settings, use the following syntax:

```txt
{FLOW.Flow name.Property name}
```

- **FLOW**: A fixed keyword to indicate that the variable represents a flow.

- **Flow name**: The name of the flow you want to reference.

- **Property name**: The property of the fed data that should be used, e.g. "Protocol Name".

> [!NOTE]
>
> - Any parts of this syntax that contain spaces should be enclosed in double quotation marks.
> - All parts of this syntax are case-sensitive.

### Example

To use the ID output of the "Selected Items Flow" flow:

```txt
The selected item is `{FLOW."Selected Items Flow".ID}`.
```
