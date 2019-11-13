[<Home](README.md)

# Mapping publication keywords with Gephi

This tutorial walks through the process of mapping the keywords for scientific publications. This is most usefull for conducting systematic literature reviews, but the tutorial can also be used as a general introduction to mapping data using network graphing techniques.

To follow this tutorial, you will need to have the network graphing tool [Gephi](https://gephi.org) installed. Once you have installed Gephi, you will need to go to Tools > Plugins and install the [Convert Excel and csv files to networks](https://gephi.org/plugins/#/plugin/excel-csv-converter-to-network) plugin.

The tutorial uses data collected from [Scopus](http://www.scopus.com). If you want to work with your own data, you will likely need institutional access to Scopus. Otherwise, you can [download the data](https://github.com/constantmethod/constantmethod.github.io/blob/master/selectedPubsMetaData.csv?raw=true) that I use in the tutorial instead.

## Getting data about publications from Scopus

To get a list of keywords to work with, we will need to search for publications. This could be done on a variety of databases, but [Scopus](http://www.scopus.com) is one of the easiest to use.

Once you have searched for a relevant topic and assembled a list of relevant publications in Scopus, check the box next to All at the top of the list to select all the publication and click on CSV export. If you have more than 2000 publications in your list, Scopus will ask you if you want the all the information for the first 2000 or just the citation information for up to 20,000. For our purposes, we only need the keywords that are part of the citation information so select that. If you click on the arrow next to CSV export, you can specify which specific information you want to export and it is interesting to look at what is available.

Once you have downloaded the CSV export or the [example data](https://github.com/constantmethod/constantmethod.github.io/blob/master/selectedPubsMetaData.csv?raw=true) I collected, you can move to Gephi.

## Making a network from lists of data

The CSV file assembled by Scopus contains alot of different columns, but the one we are interested in is Index Keywords. These are the keywords assigned by Scopus to each publication, but you could also do this with the keywords that the authors have chosen.

In Gephi, go to File > Import. Not Import spreadsheet... or Import Database, just Import. This should start the Import Wizard where you probably only have one wizard available. Make sure that under Category you have selected Data importer and under Wizards Type you have slected Convert Excel and csv files to networks. 

Click on Next and select the CSV file from Scopus. This file is a 'Comma Seperated File' meaning that there is a comma between each data field. Make sure that comma is selected as the field delimiter and that 'file includes headers' is checked, and click Next.

You should now see a dialogue asking you to select agents. Agents are data types and you should see all the data types (or columns) from your CSV file listed. This is where the list gets turned into a network and to do that we need to connect individual data points together. Since we are interested in the way keywords appear in our datset of publications, we will connect Index Keywords to Index Keywords. This means that a connection will be made between two publications when the same keyword appears for them.  Click on next.

![Import Wizard agents](https://github.com/constantmethod/constantmethod.github.io/blob/master/gephi_agents.png?raw=true)

Each publication has more than one keyword, so we need to tell Gephi how to read each keyword independently. In this case, the keywords are seperated by semicolons, so make sure that delimiter is selected for subfields and click next.

You will now be asked if you want to create a dynamic network. This means that each network connection would be associated with a time stamp, making it possible to visualize how the network changes over time. This can be done with the Scopus dataset, but just skip it for now by clicking on Next without selecting anything.

You should now see three options. Check 'create links...' to create the connections between publications with same keywords and click on 'remove self-loops' to filter out case of publications that might mistakenly have the same keyword more than once. Leave 'remove duplicates' unchecked as we are not just interested in the presence of connections, but also in the number of them. Click on Next and then on Finish on the next screen.

![Import Wizard agents](https://github.com/constantmethod/constantmethod.github.io/blob/master/gephi_selfloops.png?raw=true)

An Import Report will pop up with some errors that don't really matter for our purposes. Click on OK to display your network.

