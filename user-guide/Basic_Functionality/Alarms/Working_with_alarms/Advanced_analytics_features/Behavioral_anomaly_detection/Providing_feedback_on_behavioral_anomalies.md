---
uid: Providing_feedback_on_behavioral_anomalies
---

# Providing feedback on behavioral anomalies

> [!IMPORTANT]
> The anomaly feedback feature is in preview until DataMiner 10.4.11/10.5.0. If you use the preview version of the feature, its functionality may be different from what is described below. For more information, see [Soft-launch options](xref:SoftLaunchOptions).

The anomaly feedback feature is fully available from DataMiner 10.4.11/10.5.0 onwards<!--RN 39945-->. Prior to this, it is available in soft launch from DataMiner 10.4.4 onwards, if the soft-launch option [*AnomalyFeedback*](xref:Overview_of_Soft_Launch_Options#anomalyfeedback) is enabled<!--RN 38980 + 39944-->.

![Anomaly feedback feature](~/user-guide/images/Anomaly_Feedback.png)<br>*Alarm Console in DataMiner 10.4.11*

Whenever behavioral anomaly detection triggers a suggestion event or alarm, you can provide feedback (positive or negative) on it in the Alarm Console. Regularly providing feedback helps anomaly detection learn from it on a system-wide level, with input from all users. This allows more accurate detection of which change points to mark as anomalies across the system<!--RN 39623-->. Feedback applies to the same parameter instance, other instances of the parameter, and other elements using the same protocol.

Feedback can be provided via the ![Feedback](~/user-guide/images/Feedback_Column.png) column, which is visible by default in the *Anomalies* and *Suggestion events* tabs of the Alarm Console. To make the column visible in other tabs that list either alarms or suggestion events, right-click the column headers and select *Add or remove columns* > *Actions* > *Feedback*<!--RN 39640-->.

> [!TIP]
> See also: [*Improving anomaly detection using feedback* tutorial](xref:Anomaly_Feedback_Tutorial)

## Prerequisites

- Behavioral anomaly detection is enabled, and all its [prerequisites](xref:Advanced_analytics_trending) are met.

- [Storage as a Service (STaaS)](xref:STaaS) or an [indexing database](xref:Supported_system_data_storage_architectures).

- The [time to live](xref:Specifying_TTL_overrides) for trending is at least 1 day for real-time trending and 1 month for minute records.

## Providing feedback

<!--RN 39640-->

To provide feedback:

1. In the Alarm Console, open the *Anomalies* or *Suggestion events* tab. See [Navigating the light bulb menu](xref:Light_Bulb_Feature#navigating-the-light-bulb-menu) and [Adding a tab](xref:ChangingTheAlarmConsoleLayout#adding-a-tab).

1. Verify that the ![Feedback](~/user-guide/images/Feedback_Column.png) column is visible. If it is not:

   - Close the *Anomalies* or *Suggestion events* tab and reopen it. However, make sure not to use the *Reopen closed alarm lists* option. See [Adding a tab](xref:ChangingTheAlarmConsoleLayout#adding-a-tab).

     This step might be necessary if you have recently upgraded from a version of DataMiner that did not include the Feedback column to one that does (DataMiner 10.4.11/10.5.0 or higher). Since Cube saves your open tabs along with their column layout, the new column will not automatically appear in tabs that were open before the upgrade.

   - Ensure you are using DataMiner version 10.4.11/10.5.0 or higher, or confirm that the *AnomalyFeedback* option is included in the *SoftLaunchOptions.xml* file.

   - If possible, manually add the column by right-clicking the column headers and selecting *Add or remove columns* > *Actions* > *Feedback*.

1. Hover the mouse pointer over a suggestion event or alarm to view the ![Thumbs-up](~/user-guide/images/Thumbs_Up.png) and ![Thumbs-down](~/user-guide/images/Thumbs_Down.png) icons.

   - If you want to be notified of similar anomalies in the future, click the thumbs-up icon in the feedback column. Alternatively, you can right-click the suggestion event/alarm and select *Like*.

   - If you do not want to be notified of similar events in the future, click the thumbs-down icon. Alternatively, you can right-click the suggestion event/alarm and select *Dislike*.

   Once selected, the chosen icon will be pinned in the column as a black icon. If you change your mind, you can click the other option, and only the final feedback will be registered<!--RN 39082-->.

   > [!NOTE]
   >
   > - The ![Thumbs-up](~/user-guide/images/Thumbs_Up.png) or ![Thumbs-down](~/user-guide/images/Thumbs_Down.png) icons will only appear for alarms or suggestion events generated by the behavioral anomaly detection feature.
   > - You can only see the feedback icons you have clicked yourself. Feedback from other users is not visible.

The feedback you provide will be taken into account in the future.

Feedback on active alarms is saved in the user settings and will re-appear after Cube is closed and reopened. Feedback on history alarms will disappear after Cube is restarted, but it will still be used by SLAnalytics to improve the detection of future anomalies.

## Follow-up actions after providing feedback

After you have provided feedback on a suggestion event or alarm, a light bulb icon may appear next to the ![Feedback](~/user-guide/images/Feedback_Column.png) column. Clicking this icon will reveal a follow-up action based on your feedback<!--RN 39809 + 39640 + 39480-->. Alternatively, you can right-click the suggestion event or alarm and select the follow-up action from the context menu.

| Action | Description |
|--|--|
| Clear event | Clears the suggestion event immediately. No confirmation box will appear. |
| Improve alarm template | Opens a pop-up window suggesting changes to the alarm template, based on previous feedback for the parameter. At the top of the window, you can see the element and parameter name, along with a link to relevant documentation<!--RN 39616-->. At the bottom, it shows which elements using the same alarm template will be affected by the suggested template changes<!--RN 39729-->. A clock button allows you to view the current anomaly template configuration<!--RN 39640-->. |
| Create alarm template | Opens a card to create a new alarm template from scratch. |

![Suggested actions](~/user-guide/images/Suggested_Actions.png)<br>*Alarm Console in DataMiner 10.4.11*

If you provide feedback on multiple suggestion events for the same parameter, an action will only be suggested for the last one you gave feedback on<!--RN 39640-->.

> [!NOTE]
>
> - The actions listed above will only appear if you have the required permissions to perform them. The system will not suggest updating or creating an alarm template if you do not have the following user permissions<!--RN 39480-->:
>
>   - [*Modules > Protocols & Templates > Alarm templates > UI available*](xref:DataMiner_user_permissions#modules--protocols--templates--alarm-templates--ui-available)
>   - [*Modules > Protocols & Templates > Alarm templates > Add*](xref:DataMiner_user_permissions#modules--protocols--templates--alarm-templates--add)
>   - [*Modules > Protocols & Templates > Alarm templates > Edit*](xref:DataMiner_user_permissions#modules--protocols--templates--alarm-templates--edit)
>
> - The *Improve alarm template* and *Create alarm template* actions will not appear if the element in question has an alarm template group assigned<!--RN 39666-->.
