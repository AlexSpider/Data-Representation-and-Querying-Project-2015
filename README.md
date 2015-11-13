
# Galway City Library informatione
# Data Representation and Querying Project 2015
### Oleksandr Kozytskyy
### G00279752

## Introduction
This project provides the design and documentation for the dataset "Galway City Library informatione" which is available at [data.gov.ie](https://data.gov.ie/dataset/galway-city-library-locations)

####About DataSet 
This data contain information about all librarys in Galway City the their Names, address, contact details, open hours and coordinats .
This dataset contains 4 row, the first being a header row with the names of each
field. Tree other row is information about each library in Galway city. Also it has 19 columns:

Field |	Value
------|------
**OBJECTID**| 1
**NAME**| Galway City Library
**ADDRESS**	|St. Augustine Street, Galway,
**TEL**	|00 353 91 561666
**EMAIL**|	info@galwaylibrary.ie
**MONDAY**|	2.00pm to 5.00pm
**TUESDAY**|	11.00am to 8.00pm* (*juvenile library closes at 5pm daily)
**WEDNESDAY**|	11.00am to 8.00pm* (*juvenile library closes at 5pm daily)
**THURSDAY**	|11.00am to 8.00pm* (*juvenile library closes at 5pm daily)
**FRIDAY**	|11.00am to 5.00pm
**SATURDAY**|	11.00am to 5.00pm
**Lat**	|53.272
**Long**|	-9.052
**EastITM**|	529810.631
**NorthITM**	|725090.618
**EastIG**|129844.715
**NorthIG**	|225061.41
**X**	|-9.051675534
**Y**|53.27126324

 as you can see on example of table information are very ditailed, its include open hours for each day of week and
 coordinats for different type of coordinate system:
 
 Coordinate system | Description
 ------------------|-------------
 **Long - Lat**	| [A geographic coordinate system](https://en.wikipedia.org/wiki/Geographic_coordinate_system)
**NorthITM - EastITM** |	 [The Irish Transverse Mercator (ITM)](https://en.wikipedia.org/wiki/Irish_Transverse_Mercator)
**NorthIG - EastIG** | [The Irish grid reference system](https://en.wikipedia.org/wiki/Irish_grid_reference_system#Grid_letters)
**x - y** | [A Cartesian coordinate system](https://en.wikipedia.org/wiki/Cartesian_coordinate_system)

Information to this database was publicly available, it is posted on the server and access to it is provided via the Internet URL address Example:

http://opendata.galwaycity.opendata.arcgis.com/datasets/f5eb1c5bac534669a253a46b4bc0ca8b_0?uiTab=table

Dataset stored on the server in [JSON](http://www.copterlabs.com/blog/json-what-it-is-how-it-works-how-to-use-it/) format. JSON is short for JavaScript Object Notation, and is a way to store information in an organized, easy-to-access manner. In a nutshell, it gives us a human-readable collection of data that we can access in a really logical manner.
Example of Dataset:

```json
[
  {
    "OBJECTID":1,
    "NAME":"Galway City Library",
    "ADDRESS":"St. Augustine Street, Galway,",
    "TEL":"00 353 91 561666",
    "EMAIL":"info@galwaylibrary.ie",
    "MONDAY":"2.00pm to 5.00pm",
    "TUESDAY":"11.00am to 8.00pm* (*juvenile library closes at 5pm daily)",
    "WEDNESDAY":"11.00am to 8.00pm* (*juvenile library closes at 5pm daily)",
    "THURSDAY":"11.00am to 8.00pm* (*juvenile library closes at 5pm daily)",
    "FRIDAY":"11.00am to 5.00pm",
    "SATURDAY":"11.00am to 5.00pm",
    "Lat":53.272,
    "Long":-9.052,
    "EastITM":529810.631,
    "NorthITM":725090.618,
    "EastIG":129844.715,
    "NorthIG":225061.41,
    "X":-9.051675534,
    "Y":53.27126324
  },
  {
    "OBJECTID":2,
    "NAME":"Westside Library",
    "ADDRESS":"Seamus Quirke Road, Galway.",
    "TEL":"00 353 91 520616",
    "EMAIL":"westside@galwaylibrary.ie",
    "MONDAY":"Closed",
    "TUESDAY":"11.00am to 8.00pm",
    "WEDNESDAY":"11.00am to 8.00pm",
    "THURSDAY":"11.00am to 5.00pm",
    "FRIDAY":"11.00am to 5.00pm",
    "SATURDAY":"11.00am to 1.00pm and 2.00pm to 5.00pm",
    "Lat":53.278,
    "Long":-9.074,
    "EastITM":528364.439,
    "NorthITM":725804.58,
    "EastIG":128398.208,
    "NorthIG":225775.516,
    "X":-9.073516271,
    "Y":53.27748604
  },
  {
    "OBJECTID":3,
    "NAME":"Ballybane Library",
    "ADDRESS":"Castlepark Road, Ballybane, Galway.",
    "TEL":"00 353 91 380590",
    "EMAIL":"ballybane@galwaylibrary.ie",
    "MONDAY":"Closed",
    "TUESDAY":"11:00 to 13:00 and 14:00 to 17:00",
    "WEDNESDAY":"11:00 to 13:00 and 14:00 to 17:00",
    "THURSDAY":"11:00 to 13:00 and 14:00 to 17:00",
    "FRIDAY":"11:00 to 13:00 and 14:00 to 17:00",
    "SATURDAY":"11:00 to 13:00 and 14:00 to 17:00",
    "Lat":53.285,
    "Long":-9.001,
    "EastITM":533237.471,
    "NorthITM":726568.725,
    "EastIG":133272.29,
    "NorthIG":226539.855,
    "X":-9.000612875,
    "Y":53.28498886
  }
]
```
Parse the JSON text returned by the server in hndataset.html to turn it into a JavaScript object.

Example:
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Hacker News API</title>
</head>

<body>

  <h1>Here's what Hacker News sent:</h1>

  <p id="hn"></p>

  <script type="text/javascript">
    xmlhttp = new XMLHttpRequest();
    xmlhttp.onreadystatechange = function() {
      if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
        ids = JSON.parse(xmlhttp.responseText);
        document.getElementById("hn").innerHTML = ids;
      }
      else
        document.getElementById("hn").innerHTML = "Error";
    };
    xmlhttp.open("GET", "https://hacker-news.firebaseio.com/v0/topstories.json?print=pretty", true);
    xmlhttp.send();
  </script>
</body>

</html>
```

The Hypertext Transfer Protocol (HTTP) is an application protocol for distributed, collaborative, hypermedia information systems. HTTP is the foundation of data communication for the World Wide Web. 
HTTP defines methods to indicate the desired action to be performed on the identified resource. What this resource represents, whether pre-existing data or data that is generated dynamically, depends on the implementation of the server. Often, the resource corresponds to a file or the output of an executable residing on the server. The HTTP/1.0 specification defined the GET, POST and HEAD methods and the HTTP/1.1 specification added 5 new methods: OPTIONS, PUT, DELETE, TRACE and CONNECT. By being specified in these documents their semantics are well known and can be depended upon. Any client can use any method and the server can be configured to support any combination of methods. If a method is unknown to an intermediate it will be treated as an unsafe and non-idempotent method. There is no limit to the number of methods that can be defined and this allows for future methods to be specified without breaking existing infrastructure. For example, WebDAV defined 7 new methods and RFC 5789 specified the PATCH method.

###Http Request methods.

#GET
The GET method requests a representation of the specified resource. Requests using GET should only retrieve data and should have no other effect. The W3C has published guidance principles on this distinction, saying, "Web application design should be informed by the above principles, but also by the relevant limitations.

#Example:
GET /index.html HTTP/1.1
http://opendata.galwaycity.opendata.arcgis.com/datasets/f5eb1c5bac534669a253a46b4bc0ca8b_0?uiTab=table

A successful request will be indicated by a 200 OK HTTP status code. The response will contain the data being retrieved:
```json
[
  {
    "OBJECTID":1,
    "NAME":"Galway City Library",
    "ADDRESS":"St. Augustine Street, Galway,",
    "TEL":"00 353 91 561666",
    "EMAIL":"info@galwaylibrary.ie",
    "MONDAY":"2.00pm to 5.00pm",
    "TUESDAY":"11.00am to 8.00pm* (*juvenile library closes at 5pm daily)",
    "WEDNESDAY":"11.00am to 8.00pm* (*juvenile library closes at 5pm daily)",
    "THURSDAY":"11.00am to 8.00pm* (*juvenile library closes at 5pm daily)",
    "FRIDAY":"11.00am to 5.00pm",
    "SATURDAY":"11.00am to 5.00pm",
    "Lat":53.272,
    "Long":-9.052,
    "EastITM":529810.631,
    "NorthITM":725090.618,
    "EastIG":129844.715,
    "NorthIG":225061.41,
    "X":-9.051675534,
    "Y":53.27126324
  },
```
#HEAD
The HEAD method asks for a response identical to that of a GET request, but without the response body. This is useful for retrieving meta-information written in response headers, without having to transport the entire content.
POST
The POST method requests that the server accept the entity enclosed in the request as a new subordinate of the web resource identified by the URI. The data POSTed might be, for example, an annotation for existing resources; a message for a bulletin board, newsgroup, mailing list, or comment thread; a block of data that is the result of submitting a web form to a data-handling process; or an item to add to a database.
PUT
The PUT method requests that the enclosed entity be stored under the supplied URI. If the URI refers to an already existing resource, it is modified; if the URI does not point to an existing resource, then the server can create the resource with that URI.
Example:
```
curl -X PUT -d '{
    "OBJECTID":1,
    "NAME":"New Galway City Library",
    "ADDRESS":"St. Augustine Street, Galway,",
    "TEL":"00 353 23 123456",
    "EMAIL":"info@newgalwaylibrary.ie",
    "MONDAY":"2.00pm to 5.00pm",
    "TUESDAY":"11.00am to 8.00pm* (*juvenile library closes at 5pm daily)",
    "WEDNESDAY":"11.00am to 8.00pm* (*juvenile library closes at 5pm daily)",
    "THURSDAY":"11.00am to 8.00pm* (*juvenile library closes at 5pm daily)",
    "FRIDAY":"11.00am to 5.00pm",
    "SATURDAY":"11.00am to 5.00pm",
    "Lat":63.272,
    "Long":-10.052,
    "EastITM":729810.631,
    "NorthITM":925090.618,
    "EastIG":229844.715,
    "NorthIG":325061.41,
    "X":-10.051675534,
    "Y":73.27126324
  },'
  ```
  http://opendata.newgalwaycity.opendata.arcgis.com/datasets/f5eb1c5bac534669a253a46b4bc0ca8b_0?uiTab=table

DELETE
The DELETE method deletes the specified resource.
TRACE
The TRACE method echoes the received request so that a client can see what (if any) changes or additions have been made by intermediate servers.
OPTIONS
The OPTIONS method returns the HTTP methods that the server supports for the specified URL. This can be used to check the functionality of a web server by requesting '*' instead of a specific resource.
CONNECT
The CONNECT method converts the request connection to a transparent TCP/IP tunnel, usually to facilitate SSL-encrypted communication (HTTPS) through an unencrypted HTTP proxy. See HTTP CONNECT tunneling.
PATCH
The PATCH method applies partial modifications to a resource.

All general-purpose HTTP servers are required to implement at least the GET and HEAD methods, and, whenever possible, also the OPTIONS method.

###Conclusion

[Application programming interface](https://en.wikipedia.org/wiki/Application_programming_interface)
In computer programming, an application programming interface (API) is a set of routines, protocols, and tools for building software applications. An API expresses a software component in terms of its operations, inputs, outputs, and underlying types. An API defines functionalities that are independent of their respective implementations, which allows definitions and implementations to vary without compromising the interface. A good API makes it easier to develop a program by providing all the building blocks. The programmers then put the blocks together.

In addition to accessing databases or computer hardware, such as hard disk drives or video cards, an API can ease the work of programming GUI components. For example, an API can facilitate integration of new features into existing applications (a so-called "plug-in API"). An API can also assist otherwise distinct applications with sharing data, which can help to integrate and enhance the functionalities of the applications.

APIs often come in the form of a library that includes specifications for routines, data structures, object classes, and variables. In other cases, notably SOAP and REST services, an API is simply a specification of remote calls exposed to the API consumers.

The simplicity and functionality of this type of API can be used for other datasets with minor changes and completion.





