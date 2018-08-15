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

![Open Web Scraper](https://github.com/rocketboytom/TEfL/blob/master/open_webscraper.png?raw=true){:height="75%" width="75%"}

- If the 'Developer tools' window is on the side of the screen, follow the instructions to move it to the bottom
- You should now see the Web Scraper window at the bottom of Chrome

![Web Scraper](https://github.com/rocketboytom/TEfL/blob/master/webscraper_window.png?raw=true)

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
  - Add the 'Id' 'thread_title' and leave the 'Type' as 'Text'. We will collect the titles of all the threads listed on the page
  - Click on 'Select' under 'Selector' and run the mouse over the titles of the threads. You should see that they become highlighted in green
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

![Scrape](https://github.com/rocketboytom/TEfL/blob/master/webscraper_scraping.png?raw=true){:height="75%" width="75%"}

- A table of data should appear in the Web Scraper window, but if it doesn't click 'Refresh'

```What is the problem with the data table?```

## Collecting data for the way you want it organised

- Go back to the Web Scraper menubar, click on 'Sitemap gardening' and choose 'Selectors'
- We need a way to group the data we are collecting so that each thread has its last reply date and number of replies associated with it and there is an easy way to do that
  - Start by going back to 'Selectors' in the menubar and deleting the selectors you made
  - Click on 'Add new selector'
    - Give the new selector the name 'threads' and selector type 'Table'
    - For 'Selector' choose 'Select' and click within the table of threads
    - The 'Header row selector' and 'Data row selector' should automatically populate
    - Don't forget to check 'Multiple' and click 'Save selector'
  - Click on 'Sitemap the_local', 'Scrape' to collect data again
  - A table of data should appear in the Web Scraper window, but if it doesn't click 'Refresh'
  
  ```How else might it be useful to collect the data in the table? What is the dataset missing?```
  
  ## Drilling down & crawling links
  
- Go back to the Web Scraper menubar, click on 'Sitemap gardening', choose 'Selectors' and delete 'threads
- Add a new selector of type 'Link' called 'thread' that collects the titles of each thread
- Click on the link to a thread with replies in Chrome so that you see the posts
- We want to group the data we collect for each post so we will use another selector type called 'Element'
  - Create an 'Element' selector called 'post'
  - Select the outer box for 2 or 3 posts - the box containing both the poster's name and the text of their post
  
![Selecting posts](https://github.com/rocketboytom/TEfL/blob/master/webscraper_post.png?raw=true){:height="75%" width="75%"}
  
  - Before clicking on 'Save selector', change 'Parent Selectors' to 'thread'
  - Now the scraper will run the new element selector for every link found by the 'thread' selector
- Now we want to fill the element selector with data from each post
  - Click on 'thread' and on 'post'
  - Add a new selector of type 'Text' called 'poster'
  - When you click on 'Select', you should see that the 1st post is highlighted yellow. Select the name of the poster from inside that post and choose 'post' as the parent selector
  - Add a text new selector for the body text of the post
- Go to the Web Scraper menubar and click on 'Sitemap gardening' and choose 'Selector graph'
  - Click on the 'root', 'thread' and 'post' nodes to expand the graph and see how the selectors fit together. For every each post in each thread the poster and body text is collected
- Select 'Scrape' from the menu bar. This scrape might take a little longer. The more pages there are to crawl, the longer it takes to scrape
- At the moment we have only scraped the 1st page of thread titles and of posts in each thread. To scrape this forum properly, we would create a link selector that crawls each page of thread tiles and then another that crawls each page of posts in a thread. We would do this using the same kind parent and child structure that we used to group the post information

## Exporting the data

![Collected data](https://github.com/rocketboytom/TEfL/blob/master/webscraper_data.png?raw=true)

- To export the data as a spreadsheet, go to 'Sitemap gardening' and choose 'Export data as CSV'
  - CSV (comma seperated values) is a standard format and will open in any spreadsheet program

```How might it be best to order the data? Is there any data missing that would be useful for creating orderings that would be good for ethnographic and interaction analyses?```
