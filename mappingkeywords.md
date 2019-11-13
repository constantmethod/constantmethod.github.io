[<Home](README.md)

# Mapping publication keywords (introduction to Gephi)

This tutorial walks through the process of mapping the keywords for scientific publications. This is most usefull for conducting systematic literature reviews, but the tutorial can also be used as a general introduction to mapping data using network graphing techniques.

To follow this tutorial, you will need to have the network graphing tool [Gephi](https://gephi.org) installed. Once you have installed Gephi, you will need to go to Tools > Plugins and install the [Convert Excel and csv files to networks](https://gephi.org/plugins/#/plugin/excel-csv-converter-to-network) plugin.

The tutorial uses data collected from [Scopus](http://www.scopus.com). If you want to work with your own data, you will likely need institutional access to Scopus. Otherwise, you can [download the data](selectedPubsMetaData.csv) that I use in the tutorial instead.

## Getting data about publications from Scopus

To get a list of keywords to work with, we will need to search for publications. This could be done on a variety of databases, but [Scopus](http://www.scopus.com) is one of the easiest to use.

Once you have searched for a relevant topic and assembled a list of relevant publications in Scopus, check the box next to All at the top of the list to select all the publications and click on CSV export. If you have more than 2000 publications in your list, Scopus will ask you if you want all the information for the first 2000 or just the citation information for up to 20,000. For our purposes, we only need the keywords that are part of the citation information so select that. If you click on the arrow next to CSV export, you can specify which specific information you want to export and it is interesting to look at what is available.

Once you have downloaded the CSV export or the [example data](https://github.com/constantmethod/constantmethod.github.io/blob/master/selectedPubsMetaData.csv) I collected, you can move to Gephi.

## Making a network from lists of data

The CSV file assembled by Scopus contains a lot of different columns, but the one we are interested in is Index Keywords. These are the keywords assigned by Scopus to each publication, but you could also do this with the keywords that the authors have chosen.

In Gephi, go to File > Import. Not Import spreadsheet... or Import Database, just Import. This should start the Import Wizard where you probably only have one wizard available. Make sure that under Category you have selected Data importer and under Wizards Type you have selected Convert Excel and csv files to networks. 

Click on Next and select the CSV file from Scopus. This file is a 'Comma Seperated File' meaning that there is a comma between each data field. Make sure that comma is selected as the field delimiter and that 'file includes headers' is checked, and click Next.

You should now see a dialogue asking you to select agents. Agents are produced from the fields of a particular data type and you should see all the data types (or columns) from your CSV file listed. This is where the list gets turned into a network and to do that we need to connect individual data fields together. Since we are interested in the way keywords appear in our datset of publications, we will connect Index Keywords to Index Keywords. This means that a connection will be made between two publications when the same keyword appears for them.  Click on Next.

![Import Wizard agents](https://github.com/constantmethod/constantmethod.github.io/blob/master/gephi_agents.png?raw=true)

Each publication has more than one keyword so we need to tell Gephi how to read each keyword independently. In this case, the keywords are seperated by semicolons so make sure that delimiter is selected for subfields and click Next.

You will now be asked if you want to create a dynamic network. This means that each network connection would be associated with a time stamp, making it possible to visualize how the network changes over time. This can be done with the Scopus dataset, but just skip it for now by clicking on Next without selecting anything.

You should now see three options. Check 'create links...' to create the connections between publications with same keywords and click on 'remove self-loops' to filter out case of publications that might mistakenly have the same keyword more than once. Leave 'remove duplicates' unchecked as we are not just interested in the presence of connections, but also in the number of them. Click on Next and then on Finish on the next screen.

![Import Wizard agents](https://github.com/constantmethod/constantmethod.github.io/blob/master/gephi_selfloops.png?raw=true)

An Import Report will pop up with some errors from missing data that don't really matter for our purposes. Click on OK to display your network.

## Laying out the network with Gephi

Once you have created a network from the list of keywords, you will probably see a mess of dots and lines on the screen. We now need to layout the network in a way that reveals its properties.

![Import Wizard agents](https://github.com/constantmethod/constantmethod.github.io/blob/master/gephi_mess.png?raw=true)

Start by going to the Layout window and choosing a Layout. There are many different layout algorithms for visualising networks, but for our purposes, ForceAtlas2 should work well. The particular algorithm you choose depends on what you want to visualize so its worth trying them out.
 
With ForceAtlas2 selected, click on Run. Once the network has started to stabilize and isn't moving very much click on Stop. The result should still look like a clumped up mess of dots, but you should see that certain clusters are starting to appear.

![Initial network visualisation](https://github.com/constantmethod/constantmethod.github.io/blob/master/gephi_forceatlas1.png?raw=true)

ForceAtlas2 simulates gravitational and repulsion forces between the nodes (dots) in the network. The more connections between two nodes, the more gravational pull between them. To stop all the nodes from bunching together we can either adjust the Gravity or the Scaling. By default scaling is set at 2.0 and Gravity at 1.0. Try changing these values and running the algortihm to see what happens. In the end, I settled on leaving the gravity at 1.0 and changing the scaling to 50.

![Network layout](https://github.com/constantmethod/constantmethod.github.io/blob/master/gephi_forceatlas2.png?raw=true)

Now we can scale the nodes to show which are the most frequent keywords and turn on labels. To scale the nodes, look at the Appearance window in the top left and click on the icon that looks like several nested circles. Click on Ranking and choose frequency as the attribute. You can set the maximum and minimum size of the nodes and for me I chose 5 and 50. Click on Apply to see what happens to the network and adjust as necessary.

To turn on labels, look at the very bottom of the Graph window and click on the large black T. You should now see all the labels (keywords) on the graph, but they are likely all on top of each other. They can be scaled in the same way as the nodes with most frequent appearing largest. To do this click on the icon that looks like two Ts in the Appearance window, select ranking and choose Frequency as the attribute. Again, you can decide on the minimum and maximum sizes of the labels and I settled on 0.5 and 2.

![Label size](https://github.com/constantmethod/constantmethod.github.io/blob/master/gephi_forceatlas3.png?raw=true)

The network graph is starting to look interesting, but it needs tweaking to make it easier to read. To prevent the labels from overlapping with each other, go back to the Layout window and select the Label Adjust algorithm. Run it and watch how the network adjusts slightly so that the labels aren't on top of each other. The problem now is that everything is black, making labels difficult to read. To change this, go to the Appearance window and click on the icon that looks like a painter's palette. You should come to the Nodes > Unique tabs by default with a grey colour showing. Click on apply. The nodes (dots) and edges (lines) in the network should change to grey making it much easier to see the labels.

![Recolour network](https://github.com/constantmethod/constantmethod.github.io/blob/master/gephi_forceatlas4.png?raw=true)

At this point, you should have a usable visualisation that reveals how different keywords are clustered together and which occur most frequently. However, to make a prettier version that can be exported at high resolution, click on the Preview button at the top of the screen. Gephi will change to a different part of the program where new tools for polishing the presentation of your network are available. This part does not update automatically so everytime you want to see the effect of changes you have made, you need to click on Refresh at the bottom of the screen.

Under Presets in the upper left of the screen, select Default Straight and refresh the screen. You may notice that the labels are under the nodes, so select the Manage Renderers tab and move Default node labels to the top of the list.

![Renderer order](https://github.com/constantmethod/constantmethod.github.io/blob/master/gephi_preview1.png?raw=true)

It would be good if the labels fit better so go back to the Settings tab and uncheck Proportional size under Node Labels. Now you can change the the size of the labels by clicking on the elipses beside Font. The font size you choose will be the maximum size for the labels with the others proportionally smaller following the rule you set earlier in the Overview part of Gephi. For this example, Arial 36 Plain works well. At this size you can read all the labels and the most frequent ones are not too large.

When you are happy with your visualisation, you can export it by clicking on the Export: SVG/PDF/PNG button at the very bottom left of the screen.

![Gephi output](https://github.com/constantmethod/constantmethod.github.io/blob/master/gephi_output.png?raw=true)
