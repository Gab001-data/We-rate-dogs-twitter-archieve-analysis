## We Rate Dogs Twitter Archieve Analysis

The goal of this project is to demonstrate data wraggling skills for accurate and reliable data analysis. Real-world data rarely comes clean. Using Python and its libraries, we will gather data from a variety of sources (manual download, cloud sources and twitter data) and in a variety of formats, assess its quality and tidiness, then clean it. we will then perform exploratory analysis on the cleaned data. The dataset that we will be wrangling (and analyzing and visualizing) is the tweet archive of Twitter user @dog_rates, also known as WeRateDogs. WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. These ratings almost always have a denominator of 10. The numerators, though? Almost always greater than 10. 11/10, 12/10, 13/10, etc. This archive contains basic tweet data; tweet ID, timestamp, text, etc.

## Installations
Since Anaconda comes with all the neccessary analytical package installed including Ipython notebook, we recommend installing Anaconda. Refer to the installation instructions [here](https://docs.anaconda.com/anaconda/install/).

```
conda install pandas numpy matplotlib seaborn

pip install tweepy

```

## Workflow
Our task in this analysis covers;
1. Gathering data

2. Assessing data

3. Cleaning data

4. Storing data

5. Analyzing, and visualizing data

Check the [Jupyter Notebook]() for detailed workthrough for each stage of the analytical process.

## Mining Tweet Data
In this analysis we scrap additional tweet data for archived WerateDogs tweet IDs using Tweepy api client. use the below code to mine tweet data.

```
import tweepy

consumer_key = 'YOUR CONSUMER KEY'
consumer_secret = 'YOUR CONSUMER SECRET'
access_token = 'YOUR ACCESS TOKEN'
access_secret = 'YOUR ACCESS SECRET'

# authenticating the request
auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_secret)

api = tweepy.API(auth, wait_on_rate_limit=True, wait_on_rate_limit_notify=True )

```
Note that you will need to setup a twitter developer account with elevate access for authentication to be able to query twitter data using the above code. click [here](https://developer.twitter.com/en/support/twitter-api/developer-account) to setup developer account.

## JSON
The request to twitter API returns a json object containing basic tweet data as shown below. this data is written to text file for all archived tweet Ids.

```
{'created_at': 'Tue Aug 01 16:23:56 +0000 2017',
 'id': 892420643555336193,
 'id_str': '892420643555336193',
 'full_text': "This is Phineas. He's a mystical boy. Only ever appears in the hole of a donut. 13/10 https://t.co/MgUWQ76dJU",
 'truncated': False,
 'display_text_range': [0, 85],
 'entities': {'hashtags': [],
  'symbols': [],
  'user_mentions': [],
  ...}
```
## Data Integrity Issues
### Quality Issues
`Twitter archive` table

1. Extraneous data; retweets and reply part of archive dataset.

2. Incorrect dog name "a" as a result of erroneous extractions or non-dog rating tweets.

3. Missing dog name/ dog stages. This will be handled in issue 1.

4. Columns contains invalid type "None".

5. timestamp column is of type str and not datetime.

6. Incorrect numerator rating of 1776 for Atticus.

7. Missing tweet data (favorite and retweet count) for tweet_id in twitter_archive. mostly for deleted tweet data.

`image_predictions` table

8. Inconsistent case; p1, p2, p3 columns contains lowercase sometime and capitalized other times.

9. p1, p2, p3 columns are str data type instead of category.

10. predicted dog name column p1, p2, p3 contains names other than dog names. this will be taking care of when addressing tidiness issues

## Tidiness Issues
`Twitter archieve` table

1. dog stages in different columns doggo, floofer, pupper, and puppo

`Image prediction`table
2. more than one dog breeds predictions p1, p2, p2 for different confidence level
`Tweet dataset`

3. column title for tweet id id differs from all the other datasets

4. tweets_df dataset is of thesame observation type as twitter_archive

## Insights
From the analysis and visualization of the wrangled @WeRateDogs twitter archive data, we derived the following insights.

1. Golden retriever is the most popular breed based on the number of tweets that contains pictures of this breed. this may be due to their varsitile utility in hunting, field work, as guides for the blind, and in search-and-rescue. A total of 109 record in our tweet archive contain the Golden retriever breed data. if you want a dog preferred by most people that you can engage in sport activities then this breed is for you.

2. The English Springer spaniel dogs are the most adorable breed as seen by the highest average likes(favorite) per tweet. one reason for this may be because spaniels are sport dogs that are activity driven. photos of these dogs engaging in sport activities will be an adorable sight and hence receive more likes.

3. The Clumber breed has the highest average rating numerator of 27.0

4. There is a strong positive relationship between the likability (favorite count) of a dog tweet and the count of retweets it receives from other twitter users. the higher the retweets the higher the favorite count as more users can view and like the tweet due to increased exposure.

**_it is important to note that these insights are tentative as we do not have enough data to draw the above conclusions._**

## Limitations
- The dog stage wasn't considered in this analysis as this information is not available for a significant portion of our twitter archive data. considering this variable would not have provided accurate representation of our data.
- Due to the inconsistence tweet text format from which dog names were extracted, a few of records in the twitter archive had incorrect dog name and were dropped from our dataset since they were insignificant.

## Relevant Links
[Jupyter Notebook]()
[Linkedln](https://www.linkedin.com/in/gabriel-ogih-609a091a1/)
[Twitter](https://twitter.com/dev_gabby)
[Medium Article]()
