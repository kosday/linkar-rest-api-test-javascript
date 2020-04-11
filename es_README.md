# Linkar REST API Test

Este ejemplo permite probar las diferentes llamadas que se pueden realizar a Linkar REST API. A través de su código también se puede ver el proceso que se debe seguir para realizar las llamadas correctamente.

Para realizar una llamada a Linkar REST API necesitamos dos cosas:

URL: esta url hace referencia a la dirección web (host y puesto) donde Linkar Manager esta escuchando solicitudes http 

API Key: esta clave se debe crear en Linkar Manager y definir en él las direcciones IPs y las operaciones permitidas para este cliente

Una vez tenemos estos dos valores podemos fijarnos en el código javascript de este ejemplo. 

La función de Linkar utilizada es SendCommand() y su objetivo es realizar una llamada POST el servicio web proporcionado por Linkar Manager.

Esta solicitud se realizará a la URL de la operación que queramos realizar, por ejemplo, si deseamos ejecutar una READ, deberemos llamar a la URL de Linkar manager y añadirle la operación a realizar (http://yourdomain.com:11200/api/read).

El listado de operaciones permitidas es el siguiente:

Read, Update, New, Delete, Select, Subroutine, Conversion, Format, Dictionaries, Execute, LkSchemas, LkSchemasSqlMode, LKSchemasDictionaries, LkProperties, LkPropertiesSqlMode, LkPropertiesDictionaries, GetTable, GetTableSqlMode, GetTableDictionaries, GetTableNone, GetVersion, ResetCommonBlocks.

La llamada puede realizarse en dos formatos, JSON y XML, según el formato elegido para realizar la comunicación la llamada variará para que el servicio web la acepte.

Los cambios que deben realizarse según el formato escogido son los siguientes:

ContentType: 

- JSON: su valor será "application/json"
- XML: su valor será "text/xml"

DataType: 
- JSON: su valor será "json"
- XML: su valor será: "text"

Data:
- JSON: debe ser un objeto JSON convertido a texto plano
- XML: una cadena de texto con formato XML

Estos son los requisitos para que la llamada sea aceptada, pero para que sea comprendida por el servicio los datos que se envían deben seguir una estructura predeterminada.

Le llamamos a esta estructura un LkCommand, si ejecutas el código de este ejemplo podrás ver con facilidad todos y cada uno de los comandos que se pueden ejecutar, pero vamos a tratar de explicar cómo se forman.

En XML debe de existir un nodo principal llamado <LkCommand>, dentro de este nodo se encontrará todo el contenido del comando.

En JSON el objeto principal es en si mismo el LkCommand y no debe definirse como una propiedad dentro de un objeto superior

Esta es la forma correcta { "APIKey" : "my_apikey", "Data": "..." }

Esta sería una forma incorrecta { "LkCommand" : { "APIKey" : "my_apikey", "Data": "..." }} 

Como se puede ver en este último ejemplo un comando necesita contener dos variables para funcionar:

APIKey: la clave proporcionada por Linkar Manager.

Data: los datos de la operación que vamos a realizar.

Data es en si mismo otro paquete embutido dentro del LkCommand y es en este donde le daremos a la operación los argumentos necesarios y opcionales para obtener el resultado deseado. 
Cada operación tiene una plantilla concreta y en el ejemplo se puede ver fácilmente como al seleccionar una operación la previsualización de la plantilla cambia.
Para consultar más información sobre todas las plantillas disponibles le recomendamos que consulte nuestro manual de ayuda (Link a la ayuda de LkSendCommand).
