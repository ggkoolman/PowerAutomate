# Get SharePoint Site Information

## Summary

This sample flow uses SharePoint REST API to collect site-related details including list names and GUIDs, sharepoint group names and IDs, names and email  addresses of site users, and lastly, all permission masks. These data will be mapped and send back to the user by email and presented in HTML tables.

![preview01](assets/preview01.png)
![preview02](assets/preview02.png)

## Applies to

* [Microsoft Power Automate](https://docs.microsoft.com/power-automate/)

## Compatibility

![Premium License](https://img.shields.io/badge/Premium%20License-Not%20Required-green.svg "Premium license not required")
![On-Premises Connectors](https://img.shields.io/badge/On--Premises%20Connectors-No-green.svg "Does not use on-premise connectors")
![Custom Connectors](https://img.shields.io/badge/Custom%20Connectors-Not%20Required-green.svg "Does not use custom connectors")

## Authors

Solution|Author(s)
--------|---------
get-sharepoint-site-information | [Gabriel Koolman](https://www.linkedin.com/in/gabrielkoolman/)

## Version history

Version|Date|Comments
-------|----|--------
1.0|September 3, 2023|Initial release

## Minimal Path to Awesome

* [Download](solution/get-sharepoint-site-information.zip) the `.zip` from the `solution` folder
* [Import](https://flow.microsoft.com/en-us/blog/import-export-bap-packages/) the `.zip` file using **My Flows** > **Import** > **Upload** within Microsoft Flow.
* After importing the flow, proceed to open the flow and expand the **Compose** action named **'Settings'** and replace the siteUrl property with your own siteUrl.

## Disclaimer

**THIS CODE IS PROVIDED *AS IS* WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**
