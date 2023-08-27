# Step-by-step guide to build the demo flow 'WorkingWithXPath' yourself
#### [By Gabriel Koolman]

### Introduction
Sometimes, when working with REST APIs, the response can be an array of objects in JSON format. To manipulate this JSON data, you can use actions such as the 'Select' action and 'Filter Array' action, or simply utilize expressions. However, this approach can be very challenging, especially if the JSON structure is complex or deeply nested. This is where converting the JSON data into XML becomes a valuable approach. XML's hierarchical and standardized format can often be easier to navigate compared to JSON. Additionally, once your data is in XML format, you can employ XPath expressions to adeptly query and extract specific elements and attributes, offering a refined and versatile method to process the information. 

In Power Automate, there's a handy expression **xml('value')** to aid this conversion. Here, **'value'** represents the string containing the JSON object you intend to convert. It's crucial to note that this JSON object should possess **only a single root property** and it mustn't be an array. If your JSON string contains double quotation marks, remember to use the backslash character **(\\)** to escape them, ensuring accurate conversion. We'll start by converting the JSON data to XML. Once in XML format, we'll use XPath expressions to query the data effectively. Finally we can revert the data back to its JSON format for subsequent use within the flow.

The **xpath(xml, xpath expression)** expression in Power Automate requires two parameters:
1) The XML on which to apply the XPath expression.
2) The XPath expression, which is like a guide or path to find specific parts of the XML data.
- The **xpath() expression** returns an XML node, nodeset or value as JSON from the provided XPath expression.
- Please note that Power Automate currently supports only **XPath version 1** out of the box. Given this, I'll be utilizing this approach in the demo.

****Download****
- **Sample JSON File**: [here](https://github.com/ggkoolman/PowerAutomate/blob/main/WorkingWithXPath/Sample%20data%20XPath%20demo.json)
- **Flow Zip File**: [here](https://github.com/ggkoolman/PowerAutomate/blob/main/WorkingWithXPath/WorkingWithXPath.zip)
  
****More information****
- More information about **xml expression** can be found [here](https://learn.microsoft.com/en-us/azure/logic-apps/workflow-definition-language-functions-reference#xml).
- More information about **XPath Version 1.0** can be found [here](https://www.w3.org/TR/1999/REC-xpath-19991116/).


### Create the flow
1\. Navigate to **`https://make.powerautomate.com`**


2\. Click **My flow**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/82c7137b-1f74-43e6-9f2a-438268191ded/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=195,480&force_format=png&width=217&wat_scale=19&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=143,208)


3\. Click **New flow**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/4dd51580-f1ff-469b-ab24-8b05dc056fc3/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=454,223&force_format=png&width=573&wat_scale=51&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=340,71)


4\. Click **Instant cloud flow**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/957e5df8-e8c9-4fd6-9bb3-d54f8f4ff044/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=511,414&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=547,467)


5\. Click **Manually trigger a flow**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/fcfd4504-0c76-46d6-8327-afa71e7b8447/ascreenshot.jpeg?tl_px=638,100&br_px=1498,581&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=402,212)


6\. Give the flow a name and click **Create**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/315a35cb-4762-4a1d-8d2e-31211cc5f9ec/user_cropped_screenshot.jpeg?tl_px=31,81&br_px=891,562&force_format=png&width=860&wat_scale=76&wat=1&wat_opacity=0.7&wat_gravity=northwest&wat_url=https://colony-recorder.s3.us-west-1.amazonaws.com/images/watermarks/FB923C_standard.png&wat_pad=695,434)


### Adding the Actions to the Flow

7\. Add a **'Compose'** action and paste the sample json data as Input. For the complete sample JSON file, visit my GitHub repository: [Full Sample JSON File on GitHub](https://github.com/ggkoolman/PowerAutomate/blob/main/WorkingWithXPath/Sample%20data%20XPath%20demo.json).


![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/9a474fec-d63f-445f-92e7-6d269ffe5091/screenshot.png?tl_px=0,0&br_px=619,324&force_format=png&width=688)


8\. Now add 2 **'Scope'** actions and name them:
- **Nested objects inside 'root' object**
- **Only 'root' object**

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/2e6cd155-2327-4512-95e1-074ebd28e028/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=1142,164&force_format=png&width=1120.0)


#### Scope 1: Only 'root' object


9\. Add a **'Compose'** action and name it **Wrap sample data inside a root object**

Next, insert the following JSON:\
\
`{
  "root": @{outputs('Sample_of_complex_JSON_nesting_of_objects_and_arrays')}
}
`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/be0908b9-846f-4a5e-9a90-85f528bdb477/screenshot.png?tl_px=0,0&br_px=629,264&force_format=png&width=688)


10\. Add another **'Compose'** action and name it **Convert JSON to XML**

Next, insert the following expression:
`@{xml(outputs('Wrap_sample_data_inside_a_root_object'))}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/0dfb4e82-7ff8-4f38-bb60-ad9293b06835/screenshot.png?tl_px=18,0&br_px=591,153&force_format=png&width=573)


11\. Now add a **'Select'** operator and name it **Return all customers**

**From:**\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers')}`

**Map**:

- **Key:** `Customers`
- **Value:** `@{json(xml(decodeBase64(item()?['$content'])))}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/a35b364e-dfea-4f2c-a9f0-39462481ce5a/screenshot.png?tl_px=15,0&br_px=640,190&force_format=png&width=625)


12\. Add **'Compose'** action and name it **Return a single array with all first names**

Next, insert the following expression:
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers/personalInfo/firstName/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/32d6c58d-66f4-425c-8b08-ac89cfee03b2/screenshot.png?tl_px=0,0&br_px=615,150&force_format=png&width=625)


13\. Add **'Compose'** action and name it **Return all email inside array**

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers/personalInfo/email/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/eab1d99c-4324-4b9c-b71b-8d98a3a57e56/screenshot.png?tl_px=12,0&br_px=585,138&force_format=png&width=573)


14\. Add **'Compose'** action and name it **Return the names of all products purchased**

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '//purchases/product/name/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/a5e4cae4-0f02-41b1-859f-32eb94adcb13/screenshot.png?tl_px=18,0&br_px=591,142&force_format=png&width=573)


15\. Add **'Compose'** action and name it **Count purchases by customer with id 007**

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), 'count(//customers[id="007"]/purchases)')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/8f88d891-c7ef-4282-acc8-3e180107f2dd/screenshot.png?tl_px=15,0&br_px=588,140&force_format=png&width=573)


16\. Add **'Compose'** action and name it **Return all reviews written by customers**

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers/reviews/text/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/5720a07a-ef9d-47cb-8a70-1302acbc8227/screenshot.png?tl_px=0,0&br_px=603,147&force_format=png&width=625)


17\. Add **'Compose'** action and name it **Return the preferred language of Yoda**

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers[personalInfo/firstName="Yoda"]/personalInfo/preferredLanguage/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/369880ee-2f0a-4b80-b926-be64a510c9a8/screenshot.png?tl_px=14,0&br_px=587,149&force_format=png&width=573)


18\. Add **'Compose'** action and name it **Return the total loyalty points of Han Solo**

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers[personalInfo/firstName="Han" and personalInfo/lastName="Solo"]/loyalty/points/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/638747d6-9777-4faf-af68-6747c6f85efe/screenshot.png?tl_px=15,0&br_px=588,153&force_format=png&width=573)


19\. Add **'Compose'** action and name it **Return customers with 'Starships' as preference category**

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers[preferences/categories="Starships"]/personalInfo/firstName/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/30d28b15-3d81-467a-8d29-72feb88c4d55/screenshot.png?tl_px=13,0&br_px=586,143&force_format=png&width=573)


20\. Add **'Compose'** action and name it **Return product rating for 'Lightsaber' by Darth Vader**

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers[personalInfo/firstName="Darth" and personalInfo/lastName="Vader"]/reviews[product/name="Lightsaber"]/rating/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/75f98269-853e-4fc9-b960-9a16dff74e0f/user_cropped_screenshot.jpeg?tl_px=2,0&br_px=532,161&force_format=png&width=529)


21\. Add **'Compose'** action and name it **Return all products purchased by Leia Organa**

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers[personalInfo/firstName="Leia" and personalInfo/lastName="Organa"]/purchases/product/name/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/e3933fe5-3a93-4f2c-af5c-914663b33581/screenshot.png?tl_px=5,0&br_px=534,143&force_format=png&width=529)


22\. Add **'Compose'** action and name it **Return the email of a customer with id 001**

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers[id="001"]/personalInfo/email/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/f427a868-4bed-4787-97b1-5631f485d277/screenshot.png?tl_px=4,0&br_px=533,115&force_format=png&width=529)


23\. Add **'Compose'** action and name it **Return all customers id**

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers/id/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/ff9beba9-837f-48ed-8eaa-ce0d9fdd5e9d/screenshot.png?tl_px=5,0&br_px=534,130&force_format=png&width=529)


24\. Add **'Compose'** action and name it **Return date of birth of all customers**

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers/personalInfo/birthdate/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/25dab917-65dd-47ba-b582-9507d4e25438/user_cropped_screenshot.jpeg?tl_px=4,0&br_px=534,119&force_format=png&width=529)


25\. Add **'Compose'** action and name it **Return the first customer with preference category 'Starships'**

Next, insert the following expression:\
`@{json(xml(decodeBase64(first(xpath(outputs('Convert_JSON_to_XML'), '/root/customers[preferences/categories="Starships"][1]'))['$content'])))}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/53aff8e1-3be6-4822-89f8-fe9de6d69e82/user_cropped_screenshot.jpeg?tl_px=4,0&br_px=534,164&force_format=png&width=529)


26\. Add **'Compose'** action and name it **Return the last customer with preference category 'Starships'**

Next, insert the following expression:\
`@{json(xml(decodeBase64(first(xpath(outputs('Convert_JSON_to_XML'), '/root/customers[preferences/categories="Starships"][1]'))['$content'])))}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/0af1dd6a-95d0-40c3-941d-9f051ce11c84/user_cropped_screenshot.jpeg?tl_px=5,0&br_px=534,147&force_format=png&width=529)


27\. Add **'Compose'** action and name it **Return the rating and text of reviews for a specific product**. In this case I'll filter on **Lightsaber** only.

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers/reviews[product/name="Lightsaber"]/rating/text() | /root/customers/reviews[product/name="Lightsaber"]/text/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/cf383be5-c8c6-4b90-bdb0-53d5a73a9728/user_cropped_screenshot.jpeg?tl_px=9,0&br_px=539,176&force_format=png&width=529)


28\. Add **'Compose'** action and name it **Return date of birth for customers with prefered language 'Galactic Basic'**.

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers[personalInfo/preferredLanguage="Galactic Basic"]/personalInfo/birthdate/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/c9f71dd1-fa9a-47c1-b4be-1e52eef9201c/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=540,140&force_format=png&width=573)


29\. Add **'Compose'** action and name it **Return the wishlist products and priority according to customer id**. In this case I'll filter on customer with **id "004"**.

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers[id="004"]/wishlist/product/name/text() | /root/customers[id="004"]/wishlist/priority/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/9dba3a27-7c79-4b95-bf72-333b1633ce26/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=547,151&force_format=png&width=573)


30\. Add **'Compose'** action and name it **Return loyalty points where loyalty status eq 'Jedi Master'**.

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers[loyalty/status="Jedi Master"]/loyalty/points/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/8419256e-f8e5-4840-9645-28a3fe4676a1/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=541,126&force_format=png&width=573)


31\. Add **'Compose'** action and name it **Return names of customers who purchased a 'Lightsaber'**.

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers[purchases/product/name="Lightsaber"]/personalInfo/firstName/text() | /root/customers[purchases/product/name="Lightsaber"]/personalInfo/lastName/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/9f02ed68-5f75-4b22-a477-5ee01b38ab27/user_cropped_screenshot.jpeg?tl_px=0,0&br_px=543,191&force_format=png&width=625)


32\. Add **'Compose'** action and name it **Return preferred colors when loyalty points greater than 20000**.

Next, insert the following expression:\
`@{xpath(outputs('Convert_JSON_to_XML'), '/root/customers[loyalty/points > 20000]/preferences/colors/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-22/b98ff0e3-2a87-4533-8f9e-2db0fb57196f/screenshot.png?tl_px=0,0&br_px=546,132&force_format=png&width=860)

#### Scope 2: Nested objects inside 'root' object


33\. Add a 'Select' operator and name it **Select - email**

**From:**\
`@{outputs('Sample_of_complex_JSON_nesting_of_objects_and_arrays')?['customers']}`

**Map:**

- **Key:** `email`
- **Value:** `@trim(item()?['personalInfo']?['email'])`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-27/50f5dc67-8466-418e-b08c-bbcd9a2bff5a/screenshot.png?tl_px=0,0&br_px=588,266&force_format=png&width=860)


34\. Add a 'Select' operator and name it **Select - id**

**From:**\
outputs('Sample_of_complex_JSON_nesting_of_objects_and_arrays')?\['customers'\]

**Map:**

- **Key:** `id`
- **Value:** `@item()?['id']`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-27/19ee3070-516c-401a-957f-dc4b8b327f4f/screenshot.png?tl_px=0,0&br_px=540,191&force_format=png&width=860)


35\. Add a **'Compose'** action and name it **Wrap sample data inside a root object 1**

Next, insert the following JSON:

`{
  "root": {
    "email": @{body('Select_-_email')},
    "id": @{body('Select_-_id')}
  }
}
`
![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-27/45da2065-4f05-40ba-928e-7fc316d55233/screenshot.png?tl_px=0,0&br_px=541,233&force_format=png&width=860)


36\. Add **'Compose'** action and name it **Return all email inside array 1**.

Next, insert the following expression:\
`@{xpath(xml(outputs('Wrap_sample_data_inside_a_root_object_1')), '/root/email/email/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-27/9371a763-b031-4d66-8c1e-c3647da3503d/screenshot.png?tl_px=0,0&br_px=542,125&force_format=png&width=860)


37\. Add **'Compose'** action and name it **Return all id inside array**.

Next, insert the following expression:\
`@{xpath(xml(outputs('Wrap_sample_data_inside_a_root_object_1')), '/root/id/id/text()')}`

![](https://ajeuwbhvhr.cloudimg.io/colony-recorder.s3.amazonaws.com/files/2023-08-27/fe5c4e6c-9a7b-4d83-aa48-272606c8cc6b/screenshot.png?tl_px=0,0&br_px=538,123&force_format=png&width=860)

#### --END--
