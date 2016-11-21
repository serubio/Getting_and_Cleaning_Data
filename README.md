# Getting_and_Cleaning_Data

## Week 1
Before we collect the data it is advisable to create a directory to save it.
~~~
if (!file.exists("data")) {
	dir.create("data")
}
~~~
**Downloading files**

In order to get data from the internet we use the download.file() function

~~~
fileUrl <- "https://data.link/to/data"
download.file(fileUrl, destfile = "./data/data_name.csv)
dateDownloaded <- date() # This way we know when we downloaded the data. We could go back and find the 
data if we were having trouble later on
dateDownloaded
~~~
