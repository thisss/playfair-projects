# DIARY
- After the intense last project, I wanted to do a simpler one. I have chosen a existing dataset. I was unaware of all the troubles, I could run into with this data. 
- First challenge: [The dataset](https://www.pxweb.bfs.admin.ch/Selection.aspx?px_language=de&px_db=px-x-1103020100_104&px_tableid=px-x-1103020100_104%5cpx-x-1103020100_104.px&px_type=PX) is big. It can only be downloaded in parts over the convenient web interface. Therefore I fist downloaded the full data. It was in the PC Axis Format (px). I did look for a converter for Python/ Pandas first, but couldn't get one to work. I also tried to follow the manual way from [this blog post](https://exversiondata.wordpress.com/2014/06/17/obscure-data-formats-px-files/). Since the structure of the file is complicated, I finally decided to try another way: There is a importer for R available. I installed pxR and managed to read in and export the data again. The necessary steps: 
	- library("pxR")
	- my.px.object <- read.px("/home/this/Dokumente/bz/ny/data_studio/projects/4_road/data/px_car.px")
	- my.px.data <- as.data.frame(my.px.object)
 	- write.csv(MyData, file = "MyData.csv")
- This seemed to work at first sight: There was data available. A lot of data: The file inflated to 6.5 Gigabyte. Unfortunately, the data was strange. There were more or less the same number of occurences for all categories. And a couple of expected columns like the number of seats were missing. I decided to download the files for each year seperately, do the necessary corrections (take off the header). 
- The encoding was not UTF-8. I did have to import it with the right parameter in order not to loose the "Umlaute". 
- Finally, I was able to start to work with the data. 
- Later, I had to import information about the [population of each canton](http://www.bfs.admin.ch/bfs/portal/de/index/infothek/onlinedb/stattab/01.topic.9.html). This was not a quick import either, since the available files at Swiss Statistics are splitted in two: up to 2010 and after 2010. These two files are structured in a different way. It took me hours to merge the data. One of the main issues was a problem with the header of the index.
- Finally, I created some graphs about the data.
