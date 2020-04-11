# Linkar REST API Test
This example allows you to test the different calls that can be made to the Linkar REST API. The process that must be followed to make the calls correctly can also be seen through your code.

We need two things to make a Linkar REST API call:

URL: This url refers to the web address (host and position) where Linkar Manager listens for http requests.

API Key: This key must be created in Linkar Manager and defines the  IP addresses and operations allowed for this key in it.

Once we have these two values, we can look at the javascript code in this example.

Linkar REST API uses all Linkar Sendcommand Function Templates:
READ, UPDATE, NEW, DELETE, SELECT, SUBROUTINE, CONVERSION, FORMAT, DICTIONARIES, EXECUTE, LKSCHEMAS, LKSCHEMASSQLMODE, LKSCHEMASDICTIONARIES, LKPROPERTIES, LKPROPERTIESSQLMODE, LKPROPERTIESDICTIONARIES, GETTABLE, GETTABLESQLMODE, GETTABLEDICTIONARIES, GETTABLENONE, GETVERSION, RESETCOMMONBLOCKS.

The call can be made in two formats, JSON and XML, the call will vary depending on the format chosen to make the communication, so that the web service accepts it.

You must change the following according to the chosen format:
•	ContentType: 
JSON: value "application/json".
XML: value "text/xml".
•	DataType: (not necessary in all languages)
JSON: value "json".
XML: value "text".
•	Data:
JSON: It must be a JSON object converted to plain text.
XML: Text string in XML format.

These are the requirements for the call to be accepted, but the data sent must follow a predetermined structure for the service to be understood.
We call this structure an LkCommand. If you execute the code in this example, every command that can be executed will be easily seen. Let's try to explain how they are formed.
There must be a main node called <LkCommand> in XML. All the content of the command will be found inside this node.
In JSON the main object is the LkCommand itself and must not be defined as a property within a parent object.
Wrong: { "LkCommand" : { "APIKey" : "my_apikey", "Data": "..." }} 
Right: { "APIKey" : "my_apikey", "Data": "..." }

A command needs to contain two variables to work, as you can see in this example:
APIKey: The APIKey provided by Linkar Manager.

Data: The data of the operation that we are going to carry out.

Data is itself another package embedded within the LkCommand, and it is here where the operation necessary and optional arguments to obtain the desired result will be given.
Each operation has a specific template. In these examples, we will use the READ operation template.
We recommend you consult the help manual for information on all available templates.



