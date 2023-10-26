# SharePoint REST API Crud Operations in Power Automate

## Summary

This sample solution covers CRUD operations when using SharePoint REST API inside Power Automate. It is intended to serve as a valuable reference for interacting with the SharePoint REST API within Power Automate.

## Flows

* create-item-in-another-list
* update-item-in-another-list

#### create-item-in-another-list
This flow illustrates the process of creating a new list item in a secondary list (Target List) from a source list (CreateList) using the 'Send an HTTP request to SharePoint' action in Power Automate. It covers commonly used fields including: Content Type, Date, Date and Time, Hyperlink, Multi-select Choice, Multi-select People Picker, Number, Single Choice, Single Line of Text, Single People Picker, and Yes/No. Additionally, this flow can handle null values from these fields efficiently.

![preview01](assets/preview01.png)

#### update-item-in-another-list 
This flow illustrates the process of updating an existing list item in a secondary list (Target List) from a source list (CreateList) using the 'Send an HTTP request to SharePoint' action in Power Automate. It covers commonly used fields including: Content Type, Date, Date and Time, Hyperlink, Multi-select Choice, Multi-select People Picker, Number, Single Choice, Single Line of Text, Single People Picker, and Yes/No. Additionally, this flow can handle null values from these fields efficiently.

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
crud-sharepoint-rest-api | [Gabriel Koolman](https://www.linkedin.com/in/gabrielkoolman/)

## Version history

Version|Date|Comments
-------|----|--------
1.0|October 22, 2023|Initial release
1.1|October 26, 2023|Added 'update-item-in-another-list' flow

## Minimal Path to Awesome

* Create a new SharePoint list and name it "CreateList"
* Add the required columns (you can find the column names and types [here](assets/sp-column-config.json))
* Using "CreateList" as a template, create a new SharePoint list and name it "TargetList"
* [Download](solution/crud-sharepoint-rest-api.zip) the `.zip` file from the `solution` folder
* Import the solution by going to the [Power Automate Portal](https://make.powerautomate.com) and clicking on **"Import Solution"**
* Configure the (4) environment variables (the SharePoint site, CreateList, TargetList and JSON settings)
* Turn on the flow

## Using the Source Code

You can also use the [Power Platform CLI](https://docs.microsoft.com/powerapps/developer/data-platform/powerapps-cli) to pack the source code by following these steps::

* Clone the repository to a local drive
* Pack the source files back into a solution `.zip` file:
  ```bash
  pac solution pack --zipfile pathtodestinationfile --folder pathtosourcefolder
  ```
  Making sure to replace `pathtosourcefolder` to point to the path to this sample's `sourcecode` folder, and `pathtodestinationfile` to point to the path of this solution's `.zip` file (located under the `solution` folder)
* Import the solution by going to the [Power Automate Portal](https://make.powerautomate.com) and clicking on **"Import Solution"**

## Disclaimer

**THIS CODE IS PROVIDED *AS IS* WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**