# Collecting & visualising data from Twitter with TAGS

Do you have Google and Twitter accounts? If not, make them or follow along with someone else.
- Go to [TAGS](https://tags.hawksey.info/get-tags/)
- Click on TAGS v6.1
- Make a copy of the document (It should open in Google Sheets - Login if you have to).

## Data types

Look at the last row under Advanced Settings. You can collect 3 types of data:
- Based on search terms
-- search/tweets - Tweets from the past 7 days that match the search term you give (could be a hashtag, name, place, etc…)
- Based on user account
-- statuses/user_timeline - Tweets posted by a particular user
-- favourites/list - Tweets favorited by a particular user
For each of these data types, you enter a search term in the box in the Enter term row. For search/tweets you enter any text string. For statuses/user_timeline and favourites/list, you enter an account name starting with @.

### What are the different research ethics standards to consider for these different types of data?

## Duration

Like most social media platforms, Twitter restricts the amount of data you can collect from their database at a given time.

Look under Advances settings at Period. Here you can choose how many days back you want to collect data for. Since Twitter caps the amount of data you can collect at one time, you may want to restrict the number of days back you collect for very active topics. The data cap is difficult to calculate, but in practice amounts to a few thousand tweets so it is rarely a problem if collecting from a specific user or for a less popular topic.

Look at the note at the bottom of the Instructions area. You can get around Twitter’s data cap if you know ahead of time what you want to collect and setup TAGS to collect repeatedly over a period of time that could be hours or days or even years. For example, if you know that a particular course or MOOC is going to be using a a certain hashtag, you can collect tweets containing that hashtag every day for the duration of the course.

### What are the research ethics considerations of collecting retrospective data versus collecting live data?

## Try collecting data based on a search term

Choose a term. It could be a name or a place or an event. It could be a hashtag, but doesn’t have to be.

But wait! How do you know what search term use?
- This is where sustained ethnographic engagement with the communities of interest is vital
- The data you get is only as relevant as the selection criteria you use allows

Take a look at Twitter and choose a hashtag or trend that you would like to examine. Decide on a search term.

- Write in the Enter term box and make sure that Type is set to search/tweets
- Go to the Google Sheets menu and choose TAGS > Run now!
- Give TAGS permission to run the script by clicking on Allow
- Give TAGS permission to use your Twitter account to collect data
-- Click on Yes to setup Twitter
-- Click on Easy Setup
-- When the new window pops up click on Review Permissions and then on Allow
-- Click on Sign in with Twitter and then on Authorise app (Login to Twitter when prompted if needed)
--Close the tab or window and go back to Google Sheets
- Go back to the menu and choose TAGS>Run Now! again. Wait until you see the Script Finished message
- Go to the bottom of the screen and choose the Archive tab to see the data you have collected

### What kind of data did you get Twitter?

## Ways of representing data
Go back to the ‘Readme/Settings’ tab at the bottom of the screen.

To do this we need to open up the dataset. In the top right corner click on Share
- Click on Advanced and then on ‘Change’ in the row with ‘Private - Only You can access’
- Change the setting to ‘On - Public on the web’
- Click on ‘Save’ and then on ‘Done’

Under ‘Make interactive’ you will see ‘TAGSExplorer’ and ‘TAGSArchive’.
- TAGSExplorer is a network graphing tool. Click on the link to it
-- Each circle (node) is a user who made a tweet including your search term
-- Solid lines (edges) represent one user replying to another’s tweet. The arrows show the direction
-- At the bottom right of the screen you can click on links to turn on representations of mentions and retweets, turn them on
--- Grey dashed lines represent mentions when one user mentions another’s name in a tweet
--- Blue dashed lines represent retweets when one user retweets (forwards) another’s tweet
-- The size of the account name represents the number of in-links a user has in the network. In this case, in links are replies, mentions and retweets. This can be interpreted as a measure of relative importance in the network

### How might a network graph inform an ethnographic study of the community of Tweeters?

TAGSArchive visualises the dataset over time and has search tools. Go back to the main TAGS Google Sheet and click on the link to it.
- The tweets are organised chronologically
- The timeline at the top has dots on it. Each dot represents a tweet and the visualisations shows volume of activity over time
- Use the bars at the edges of the timeline to select specific time periods
- The Filter boxes at the top allow you to filter tweets by the content of the tweet or the content of the user name

### How might a chronological visualisation inform an ethnographic study of the community of Tweeters?





