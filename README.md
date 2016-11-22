# Getting_and_Cleaning_Data

## Week 1
Before we collect the data it is advisable to create a directory to save it.
~~~
if (!file.exists("data")) {
	dir.create("data")
}
~~~
**Downloading files**

In order to get data from the internet we use the `download.file()` function

~~~
fileUrl <- "https://data.link/to/data"
download.file(fileUrl, destfile = "./data/data_name.csv)
dateDownloaded <- date() # This way we know when we downloaded the data. We could go back and find the 
data if we were having trouble later on
dateDownloaded
~~~

**Reading Local files**

The `read.table()` function is the main function for reading data into R. However, it reads the data into
RAM, so big data can cause problems.

~~~
data <- read.table("data.csv", sep = ",", header = TRUE)
~~~
We can also use `read.csv()` function (like read.table, it reads data into RAM)
~~~
data <- read.csv("data.csv", na.rm = TRUE)
# read.csv sets sep="," and header=TRUE automatically
# other options: skip= number of lines to skip before starting to read; nrows= how many rows of the file
# to read; quote= it helps with unwanted values, usually solves problems reading data.
~~~

**Reading Excel files**

~~~
data <- read.xlsx("data.xlsx", sheetIndex = 1, header = TRUE, colIndex = 2:3, rowIndex = 1:4)
# colIndex and rowIndex would only read those rows and columns
~~~

The XLConnect package has more options for writing and manipulating Excel files. In general it is advised
to store your data in either a database or in comma separated files (.csv) or tab separated files (.tab/.txt)
as they are easier to distribute

**Reading XML**

~~~
library(XML)
fileUrl <- "http://www.address.com/xml/some.xml
doc <- xmlTreeParse(fileUrl, useInternal = TRUE)
rootNode <- xmlRoot(doc)
xmlName(rootNode)
~~~

Example

`rootNode[[1]]`

~~~
<food>
<name>Belgian Waffles</name>
<price>$5.95</price>
<description>Two of our famous Belgian Waffles with plenty of real maple syrup</description>
<calories>650</calories>
</food>
~~~

`rootNode[[1][1]]`

~~~
<name>Belgian Waffles</name>
~~~

`xmlSApply(rootNode, xmlValue)` extracts all the tag elements of the document
``
