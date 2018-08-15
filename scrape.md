[<Home](https://rocketboytom.github.io/TEfL/)

# Scraping webforums with webscraper.io

To follow this tutorial, you will need have [Google Chrome](https://www.google.com/chrome/) installed.

[webscraper.io](https://www.webscraper.io) is a Chrome plugin for collecting data by crawling webpages written by [Mārtiņš Balodis](https://github.com/martinsbalodis).

## Setup the webscraper.io plugin

- Go to [webscraper.io](https://www.webscraper.io) in Chrome and click on 'Download Free on Chrome Store'
- Click on 'Add to Chrome' and follow the instructions
- You should see a small spidersweb logo appear to the right side of the address bar
- Click on it to see how to open 'Developer tools' where you can find webscraper.io
  - On Windows press Ctrl+Shift+I
  - On Mac press Cmd+Opt+I
- Click 'Web Scraper' in the 'Developer tools' window menu. If it does not appear in the menu, click the arrow to show more menu items
PIC
- If the 'Developer tools' window is on the side of the screen, follow the instructions to move it to the bottom
- You should now see the Web Scraper window at the bottom of Chrome
PIC

## Creating a simple scraper

- Click on 'Create a new sitemap' and 'Create sitemap'
- Choose a 'Sitemap name' in this case: gardening
- Choose a 'Start URL' in this case: https://garden.org/forums/view/gardening/
- Click on 'Create Sitemap'
- Go to https://garden.org/forums/view/gardening/ in Chrome - The forum site should appear above the Web Scraper window
- First, lets collect the links to the different discussion threads listed
  - Click on 'Add new selector'
    - A selector is an identifiable element on the webpage from which you will collect the related content
    - 'Id' is the name you will give the selector - In the end this will be the name of a data category or a column in the spreadsheet of data you produce
    - 'Type' is the kind of data you want to collect from text to images, etc...
    - 'Selector' is the webpage element you will use ot identify the data you want
  - Add the 'Id' 'thread' and leave the 'Type' as 'Text'. We will collect the names of all the threads listed on the page
PIC
  - Click on 'Select' under 'Selector' and run the mouse over the names of the threads. You should see that they become highlighted in green
    - Click on the first one and it should turn red
    - Click on the next one and you should see that not only does it turn red, but so do the remaining thread names. The system has now recognized a common identifier for that data type and has specified it in the floating box just above the Web Scraper window
      - Click on 'Done selecting!'
  - Make sure to check the 'Multiple' box under 'Selector' so that they system collects all the instances and not just one
  - Scroll down in the Web Scraper window if needed and click on 'Save selector'
- Now lets collect the date and time of the last reply made in the threads
  - Click on 'Add new selector' and this time name it 'last_reply' and leave the 'Type' as 'Text'
  - Click on 'Select', select the boxes with the last reply times until they are all highlighted, click on 'Done selecting!', don't forget to check 'Multiple' and then 'Save selector'

```How would you collect the number of replies?```

- Scrape the data you have chosen to collect by going to 'Sitemap gardening' on the Web Scaper menubar and selecting 'Scrape'
  - You can change the speed with which the scraper crawls the website and collects data, but leave these settings alone for now and click on 'Start scraping'
PIC
- A table of data should appear in the Web Scraper window, but if it doesn't click 'Refresh'

```What is the problem with the data table?```

## Collecting data for the way you want it organised

- Go back to the Web Scraper menubar, click on 'Sitemap the_local' and choose 'Selectors'
- We need a way to group the data we are collecting so that each forum has its topics and replies associated with it
  - Click on 'Add new selector'
    - Give the new selector the name 'forum' and selector type 'Link'
    - Select the links for each forum untill all are highlighted and click on 'Done selecting!'
    - Don't forget to check 'Multiple' and click 'Save selector'
  - Click on 'Edit' under 'Actions' for each of the other selectors you already created
    - For each selector, scroll down until you see the box 'Parent Selectors' and change this to 'forum'
  - The 'forum' link selector not only collects the address (URL) for each forum, but is now the parent of all the other selectors
    - Click on 'Sitemap the_local' and choose 'Selector graph' to see the organisation of the selectors
    - Click on the '_root' node, then on 'forum' and you should see the three other selectors grouped as child nodes
  - Click on 'Sitemap the_local', 'Scrape' to collect data again
  






  

  
  
  
  





