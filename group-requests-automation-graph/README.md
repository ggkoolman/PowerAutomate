# Security Group & M365 Group Requests Automation 

## Summary

This sample solution shows you how to automate security group and Microsoft 365 group requests using Power Automate, Microsoft Form and Microsoft Graph API with Application User permissions.

![preview06](assets/Preview06.png)
![preview07](assets/Preview07.png)
![preview08](assets/Preview08.png)

## Applies to

* [Microsoft Power Automate](https://docs.microsoft.com/power-automate/)
* [Microsoft Graph](https://learn.microsoft.com/en-us/graph/)
## Compatibility

![Premium License](https://img.shields.io/badge/Premium%20License-Required-green.svg "Premium license not required")
![On-Premises Connectors](https://img.shields.io/badge/On--Premises%20Connectors-No-green.svg "Does not use on-premise connectors")
![Custom Connectors](https://img.shields.io/badge/Custom%20Connectors-Not%20Required-green.svg "Does not use custom connectors")

## Authors

Solution|Author(s)
--------|---------
group-requests-automation-graph | [Gabriel Koolman](https://www.linkedin.com/in/gabrielkoolman/)

## Version history

Version|Date|Comments
-------|----|--------
1.0|September 10, 2023|Initial release

## Setup this solution

# Preparations



#### Create app registration with application user permissions


1\. Navigate to [https://entra.microsoft.com/](https://entra.microsoft.com/#home)


2\. Click on Applications and open "App registrations"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/5ba97876-1f34-447a-bed4-8e46bf4ced05/ascreenshot.jpeg?tl_px=0,224&br_px=859,705&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=137,212)


3\. Click on + New registration

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/9cd67310-4970-405b-b7df-98df9d39b606/ascreenshot.jpeg?tl_px=0,0&br_px=859,480&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=356,129)


4\. Enter a name for your application and click on "Register". I called mine Manage groups.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/8a0d2a21-93b4-4e5b-a84e-887e87c548b2/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=819,604&force_format=png&width=1120.0&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=54,1100)


5\. Click "API permissions"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/5a24720c-fea6-4ead-9ca7-bd0aa0a3f195/user_cropped_screenshot.jpeg?tl_px=0,55&br_px=576,536&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=709,558)


6\. Click "Add a permission"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/3b4dbf54-9323-4b06-9f05-762c7dd9334d/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=585,459&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=548,456)


7\. Click "Microsoft Graph"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/41c8944c-6e39-4e4b-a43d-cbb31058d40f/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=830,480&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=190,204)


8\. Click "Application permissions"

Your application runs as a background service or daemon without a signed-in user.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/abdd04df-38fb-4d47-a99e-3dc7c59b1a94/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=853,312&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=511,186)


9\. Click the "Search box" field.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/5c60321e-c049-43d9-867a-6ed4c8ef0b16/ascreenshot.jpeg?tl_px=940,126&br_px=1800,607&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=402,212)


10\. Select "User.Read.All"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/79139495-15a2-45bc-9106-be027c9c0675/ascreenshot.jpeg?tl_px=670,450&br_px=1530,931&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=402,261)


11\. Select "Group.ReadWrite.All"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/4198cba0-25f7-4c4e-bd8c-f00f44f603f3/ascreenshot.jpeg?tl_px=668,449&br_px=1528,930&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=402,212)


12\. Select "RoleManagement.ReadWrite.Directory"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/477169bd-76d3-4557-aa33-67b8fc088136/ascreenshot.jpeg?tl_px=719,450&br_px=1579,931&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=402,418)


13\. Click "Grant admin consent for.."

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/c366f2e3-ec91-44bd-b266-e99fc309dcf8/user_cropped_screenshot.jpeg?tl_px=268,195&br_px=1128,676&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=478,212)


14\. Click "Yes"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/525d37aa-d27a-4cbb-afbf-acbf23f1eef6/ascreenshot.jpeg?tl_px=175,37&br_px=1035,518&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=402,212)


15\. After the admin has given consent, you'll notice green check marks indicating that the application is allowed to use the permissions given.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/4d92a744-dbc7-43a3-859c-4c72c11c0a84/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=890,522&force_format=png&width=983)


16\. Click "Certificates & secrets"

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/e35d037c-4502-4e66-9407-35b3898be98b/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=555,477&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=661,578)


17\. Click  + New client secret

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/48966161-7018-47f1-8603-9b85ad0cb31f/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=982,508&force_format=png&width=983&wat_scale=87&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=312,370)


18\. Use a **description** if you want and set an **expiration date** that aligns with your requirements. For this demo I've selected an expiration date of 24 months.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/3109db15-6a85-4e14-9b78-4bd20675514c/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=577,326&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=1&wat_gravity=northwest&wat_url=https://colony-recorder.s3.amazonaws.com/images/watermarks/0EA5E9_standard.png&wat_pad=543,364)


19\. Make sure to note down the client secret immediately, as you won't be able to view it again once you navigate away from this page. If lose the client secret, you'll need to generate a new one.\
\
The "Value" is the client secret that you need to store.

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-09-10/fe28bd57-e498-4fea-8acf-20c00bc0d0cc/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=785,217&force_format=png&width=860)


20\. Congratulations, the app registration process is now successfully finished.

![](https://media.tenor.com/yaNqkG8o9UcAAAAC/hhgf.gif)


#### Now let's setup the Microsoft Form

**First go to https://forms.office.com/ to create the form for the solution.**

Next follow the steps as on the images and create the questions while mainting the same order. We'll adjust the form branching options at the end.
![preview03](assets/Preview03.png)
![preview04](assets/Preview04.png)
![preview05](assets/Preview05.png)

**Now edit the branching using this setup.**
![preview01](assets/Preview01.png)
![preview02](assets/Preview02.png)

#### Now let's download and import the solution.
* [Download](solution/group-request-automation-graph-api.zip) the `.zip` from the `solution` folder
* Go to https://make.powerautomate.com/
* [Import](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/import-update-export-solutions/) the `.zip` file using **Import solution** within Microsoft Power Automate Studio.

* After downloading and importing the flow: 
1) Open the trigger and the Get Response Details action, then select the form you created earlier. Using the environment variable 'FormID' is optional. It's best practice to use a datatype environment variable instead.
2) Proceed to update the following actions: **Authentication, Get additional information about requestor, Response details and Admin email**. 

## Using the Source Code

You can also use the [Power Platform CLI](https://docs.microsoft.com/powerapps/developer/data-platform/powerapps-cli) to pack the source code by following these steps::

* Clone the repository to a local drive
* Pack the source files back into a solution `.zip` file:
  ```bash
  pac solution pack --zipfile pathtodestinationfile --folder pathtosourcefolder
  ```
  Making sure to replace `pathtosourcefolder` to point to the path to this sample's `sourcecode` folder, and `pathtodestinationfile` to point to the path of this solution's `.zip` file (located under the `solution` folder)
* [Import](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/import-update-export-solutions/) the `.zip` file using **Import solution** within Microsoft Power Automate Studio.

## Disclaimer

**THIS CODE IS PROVIDED *AS IS* WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**
