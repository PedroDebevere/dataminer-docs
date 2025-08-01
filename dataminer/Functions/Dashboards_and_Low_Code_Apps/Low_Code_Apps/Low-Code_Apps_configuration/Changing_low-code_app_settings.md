---
uid: Changing_low-code_app_settings
---

# Changing low-code app settings

Low-code apps can consist of one or more pages that display the content of the application. While the [user access](xref:LowCodeApps_security_config) is set at the application level, other settings such as page and panel configuration and updates should be configured for each specific low-code app page or panel.

To change the settings of a low-code app page/panel:

1. Make sure the low-code app is in edit mode. See [Editing a low-code application](xref:Editing_custom_apps).

1. Select a page in the leftmost pane of the app editor. If you want to edit the panel settings, open the *panels* section in the page configuration pane.

1. Without selecting any of the low-code app components, in the configuration pane to the right, go to the *Settings* pane.

   If a component is selected, this pane will instead show the settings for that component. In that case, click an empty area of the low-code app first.

1. Configure the following settings as required:

   - **Page/Panel configuration**

     - *Use dynamic units*: This option determines whether parameter units will change dynamically based on their value and protocol definition, in components where this is supported.

     - *Allow components to shift*: This option determines whether components will move to make room for a component that is dragged across the low-code app page. If the option is not selected, the position of the components becomes fixed.

     - *Lazy load components*: Available from DataMiner 10.3.4/10.4.0 onwards. Select this option to make sure components are only initialized when they first appear on the screen. This will shorten the load time considerably and improve the performance of the low-code app. <!-- RN 35469 -->

       > [!NOTE]
       >
       > - This option is only available if you add the `showAdvancedSettings=true` option to the dashboard URL.
       > - Even when this option is enabled, components will not be lazy loaded in edit mode.

     - *Fit to view*: Available from DataMiner 10.2.7/10.3.0 onwards. Select this option to make sure all components are automatically adjusted to always be fully visible, so the user does not need to scroll.

     - *Number of columns*: Allows you to configure in how many columns components can be displayed in the low-code app (maximum: 50). If you change the number of columns to a lower number and the columns currently contain components, these components will be automatically relocated when necessary.

   - **Page/Panel updates**

     - *Allow WebSocket communication*: Web socket communication is enabled by default, but can be disabled, e.g. in case this is not allowed by the firewalls in your network.

     - *Fast polling timer*: The polling interval (in s) for components that display real-time information.

     - *Slow polling timer*: The polling interval (in s) for components that do not display real-time information.

1. Click the pencil icon again to leave edit mode.

1. To save your changes and publish it, click the ![Publish](~/dataminer/images/AppPublishIcon.png) icon in the header bar.

   > [!NOTE]
   > When you close a draft app you have been working on, it is saved automatically. As such, if you do not want to publish your app immediately, you can just close it to save it as a draft. However, draft apps are not shown by default on the landing page. To view them, click the cogwheel button and activate *Show draft applications*.

> [!TIP]
> See also: [Changing dashboard settings](xref:Changing_dashboard_settings)
