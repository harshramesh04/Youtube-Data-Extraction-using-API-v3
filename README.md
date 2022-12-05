

# A Comprehensive Dataset to Perform Sentimental Analysis on Youtube Video Comments
---

## About this Dataset
The majority of us have switched to social media for pleasure because of Covid. On these platforms, users who publish content receive active feedback in the form of comments, likes, and dislikes. To prepare the comment data for use by machine learning algorithms, sentiment analysis is applied to the comment data.
Our goal is to create a dataset that can assist in identifying the sentiments of such comments on the platforms' comment sections, which the relevant authorities may then utilize to make analytical judgments. We also hope to make other analyses possible by leveraging our dataset, such as time series analytics of any artist's output and the factors influencing the expansion and contraction of a creator's audience.

The dataset contains a collection of statistical information like number of likes, subscribers, views and tags. It also contains the comments extracted using the youtube's api for eaach video.

## How to use the Dataset
The dataset contains a exhaustive list of  information about each video like the number of subscribers, likes, tags, number of comments and a list of comments for each video.
It also consists of sentiments like positive, negative, neutral or compound for each video.
This dataset can be used to gain answers to the following questions-
1. What are the user's feedback after watching a video?
2. What kind of wrongful comments are being passed in a social media platform that can cause chaos?
3. How is the creator performing in terms of content which can be judged by likes and subscriber count?
4. How many of the viewers are returning viewers?

## How was the dataset created
### 1. Modules Used:
* googleapiclient.discovery.build()
* dateutil.parser()
* pandas
* numpy
* IPython.display JSON
* pprint
### 2. Process:
* Youtube Data API v3 is used in this process of creating the dataset
* A list of channel ids is created for which the comments and other video statistical data is to be extracted.
* Execute the below cell so as to connect to the api service using the api key.
* After the api service is connected, execute the cell below which contains the functions to get video ids using which video statistics can be extracted.
* There is a restriction on how many video ids and statistics can be extracted, which is a maximum of 50.
* Hence to overcome this restriction we add a loop which will keep iterating until we have reached the last page.
* This ensures that we get all the video ids for any channel.
* To call the above said functions we use a for loop so that we can keep concatinating all the data into a dataframe called 'video_dataframe' using a playlist id.
* The same way we can extract comments using the get_comments_in_videos(youtube, video_ids) and store it in a dataframe.
* Then both the dataframes are merged using a outer join on video id whihc is the primary key.
* Now we have a complete dataset which can be further taken upto pre-processing where null values, irrational data and other discripancies are eliminated.

### 3. Columns:
| Column Name   | Description   |
| ------------- | ------------- |
| Channel Title    | Unique name identifying a channel  |
| Video ID  | Unique ID identifying a video  |
| Description  | description stated by the creator for a particular video  |
| Tags  | Specific cathcy words that are used for increasing reach of the video  |
| publishedAt | Timestamp on which video was published  |
| viewCount	| Number of views  |
| commentCount | Number of Comments  |
| 	duration	| Length of the video |
| definition	 | Quality of video available |
| caption | Caption is available or not |
| 	title | Title of the video |
| 	likeCount | Number of likes |
| 	Comments | Comments extracted for that video |

### 4. Requirements:
* Youtube Data API Key
* Modules: NLTK, Pandas, Numpy, IPython.Display, Google API Client.
*  Jupytor Notebook to compile the code.

### 5. Challenges/Limitations:
* One of the challenge faced while extracting video ids is that youtube only allows a maximum of 50 results to be extratced in one go. We overcam this by creating a loop that will run until the last page is reaached.
* The youtube api has restrictions placed to the number requests that can be made. The projects that have youtube's api serivces enabled allows only 10000 units of requests to be made per project.
* We were able to extract around 60000 records containing video statistics. But, when the comments were to be extratced, the quota for the requests were exhausted.
* So to fulfill our goal to have comments and video statistics in one dataframe, we were able to extract only 9000 records atmost.

### 5. Future Improvements:
If time series  data was available then time series analysis would have been possible which we wish to accompolish in further developments.

### 6. Documents for referrence:
* Youtube Data API document: https://developers.google.com/youtube/v3/getting-started
* Youtube components extraction reference: https://developers.google.com/youtube/v3/docs
