[<Home](README.md)

# Trace ethnography as social interaction research method

## Roots
- Documentary ethnography
- Virtual/online ethnography
- Computational linguistics
- Descriptive statistics

## Key concepts
- Data collection
  - API research
    - Using a platforms Application Programming Interface to retrieve data directly from its database
    - Most platforms provide a set of API 'hooks' - different kinds of data that can be retrieved
    Computational- Requests can be specified in programming languages like Python that ask a database to return specific data from specific hooks
  - Screen scrapping
    - When an API is unavailable, a script can be written that behaves like a person visiting the pages of a website copying and pasting the content they want to collect into a spreadsheet
    
- Types of data (traces)
  - Content
    - Text
    - Images
    - Audio
    - Video
  - Meta data
    - Users
    - Timestamps

- Data processing
  - Often, the data that is collected from an API research or screen scrapping process is messy and/or needs reformating for the particular needs of a study. In this sense, data must be made from the raw material that is collected online
  - Cleaning
    - Regular expression scripts [(REGEX)](https://regexr.com)
    - Text parsing tools e.g. [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/)
  - Presenting
    - Spreadsheets
    - Chronological threading
    - Relational and graph databases

- Analysis
  - Computational
    - Exploratory data analysis
      - Content
      - Meta data
      - Calculated measures
    - Natural language processing
      - Topic modelling
      - Concordance
    - Social network analysis
      - Centrality
  - Ethnographic
    - Observation
    - Content analysis
    - Interaction analysis
    
## Example workflow
 - Collect discussion data through platform API
 - Clean up the data and format it as a speadsheet and chronological set of discussion threads
 - 

## General research ethics concerns
- From a research ethics perspective it is important to consider what data will be collected and when/what consent is needed before starting collection
  - Just because a platform makes data available, doesn't mean that any use of it is ethical!
  
## Further reading
- [Trace ethnography: a retrospective](https://ethnographymatters.net/blog/2016/03/23/trace-ethnography-a-retrospective/) by Stuart Geiger
- [Trace Interviews Step-By-Step](https://ethnographymatters.net/blog/2016/05/03/trace-interviews-step-by-step/) by Elizabeth Dubois
- Dubois, E., & Ford, H. (2015). [Trace Interviews: An Actor-Centered Approach.](http://ijoc.org/index.php/ijoc/article/view/3378) International Journal Of Communication, 9, 25.
  
  
