# **Flood Detection in Social Media Images Using Visual Features and Metadata**

> Classifying flood from the Social Media posts using Images and Text data

#### &nbsp;

## Contents

1. [Documents](#tasks)

2. [Tasks](#tasks)

3. [ML Models](#ml-models)
   
   1. [ML Model based on Image Data](c)
   2. [ML Model based on Text Data](#ml-model-based-on-text-data)

4. [Data Scraping](#data-scraping)
   
   1. [Twitter](#twitter)
   
   2. [Instagram](2.-instagram)
   
   3. [Youtube](#youtube)

5. [Contributors](#contributors-/-group-members)

&nbsp;

## Documents

- [Project Doc](https://docs.google.com/document/d/1BMo5eDfZlSXtmqdpz0cbdTknrncIBOtt8cidYivTkvg/edit#)

- [Project Presentation](https://docs.google.com/presentation/d/17e8WH02_rJ0Oej-JDc_naNgI6FqnptLRAuvpoKMdbSg)

- [Project Report](https://docs.google.com/document/d/1e2Bx4UHhPiYZP6qIY4vxFqj6tE6gU9Ecbu_def3nk8s)

&nbsp;

## Tasks

- [x] Background Research

- [x] Project Proposal

- [x] Data Collection

- [x] Data Cleanup & Dataset Preparation

- [x] Data Preprocessing

- [x] Training Model with Image Data

- [x] Training Model with Text Data [improvement required]

- [ ] Training Model with Image and Text Data

- [ ] Model Evaluation [33% done]

- [ ] Pipeline for Realtime Assessment

- [ ] Project Report / Paper Draft [Ongoing]

&nbsp;

## ML Models

##### 1.  ML Model based on Image Data

> CNN model trained using VGG16 architecture and Transfer Learning
> 
> Test accuracy : 0.9149797558784485

- [Jupyter Notebook](https://github.com/FHShubho/Flood_Assessment/blob/main/image_based_model_v2.ipynb)

- Sample Image Data
  
  ![](https://github.com/FHShubho/Flood_Assessment/blob/main/figures/sample_data_image_based_model.png)

- Data count in Train, Validation & Test Dataset
  
  ![](https://github.com/FHShubho/Flood_Assessment/blob/main/figures/data_count_image_based_model.png)

- Data Augmentation
  
  ![](https://github.com/FHShubho/Flood_Assessment/blob/main/figures/data_augmentation_image_based_model.png)

- CNN Model
  
  ![](https://github.com/FHShubho/Flood_Assessment/blob/main/figures/model_plot_image_based_model.png)

- Accuray vs. Loss Graph: Initial Training
  
  > loss: 0.6550, accuracy: 0.7820, val_loss: 0.5650, val_accuracy: 0.7918
  
  ![](https://github.com/FHShubho/Flood_Assessment/blob/main/figures/acc_loss_graph_image_based_model.png)

- Accuray vs. Loss Graph: Fine Tuning
  
  > loss: 0.1440, accuracy: 0.9414, val_loss: 0.1601, val_accuracy: 0.9265
  
  ![](https://github.com/FHShubho/Flood_Assessment/blob/main/figures/fine_tuned_acc_loss_graph_image_based_model.png)

- Predictions on Test Dataset Sample
  
  ![](https://github.com/FHShubho/Flood_Assessment/blob/main/figures/test_result_sample_image_based_model.png)

- Classification Report

|              | precision | recall | f1-score |
| ------------:| ---------:| ------:| --------:|
|              |           |        |          |
| flood        | 0.94      | 0.96   | 0.95     |
| not_flood    | 0.89      | 0.82   | 0.85     |
|              |           |        |          |
| macro avg    | 0.91      | 0.89   | 0.90     |
| weighted avg | 0.92      | 0.92   | 0.92     |

- Confusion Matrix
  
  ![](https://github.com/FHShubho/Flood_Assessment/blob/main/figures/confusion_matrix_image_based_model.png)

&nbsp;

##### 2. ML Model Based on Text Data

> Trained Only on Twitter Text Data
> 
> Training Accuracy: 87.57% & Accuray on Test Data: 84%

> 

&nbsp;

- [Jupyter Notebook](https://github.com/FHShubho/Flood_Assessment/blob/main/text_based_model.ipynb)

- Dataset Sample
  
  ![](https://github.com/FHShubho/Flood_Assessment/blob/main/figures/sample_data_text_based_model.png)

- Data count in Train and Test Set
  
  ![](https://github.com/FHShubho/Flood_Assessment/blob/main/figures/data_count_graph_text_based_model.png)

- Classification Model
  
  > using BERT(Bidirectional Encoder Representations from Transformers)
  
  ![](https://github.com/FHShubho/Flood_Assessment/blob/main/figures/model_plot_text_based_model.png)

- Classification Report

|              | precision | recall | f1-score |
| ------------:| ---------:| ------:| --------:|
|              |           |        |          |
| flood        | 1.00      | 0.20   | 0.33     |
| no_flood     | 0.78      | 1.00   | 0.88     |
|              |           |        |          |
| macro avg    | 0.89      | 0.60   | 0.60     |
| weighted avg | 0.84      | 0.79   | 0.73     |

- Confusion Matrix
  
  ![](https://github.com/FHShubho/Flood_Assessment/blob/main/figures/confusion_matrix_text_based_model.png)

&nbsp;

## Data Scraping

##### 1. Twitter

- Documentation: [Twitter API](https://developer.twitter.com/en/docs/twitter-api)
1.  Sign Up as Develeoper [HERE ](https://developer.twitter.com/en)

2. Generate required Credentials

3. Install tweepy
   `pip install tweepy`

4. Example code
   
   ```python
   import tweepy
   
   consumer_key = "XXXX" #Your API/Consumer key 
   consumer_secret = "XXXX" #Your API/Consumer Secret Key
   access_token = "XXXX"    #Your Access token key
   access_token_secret = "XXXX" #Your Access token Secret key
   
   #Pass in our twitter API authentication key
   auth = tweepy.OAuth1UserHandler(
      consumer_key, consumer_secret,
      access_token, access_token_secret
   )
   
   #Instantiate the tweepy API
   api = tweepy.API(auth, wait_on_rate_limit=True)
   
   search_query = "nasa"
   no_of_tweets =150
   
   try:
    #The number of tweets we want to retrieved from the search
    tweets = api.search_tweets(q=search_query, count=no_of_tweets)
    #print tweets
    print(tweets)
   except BaseException as e:
    print('Status Failed On,',str(e))
   
   ```

5. Example response
   
   ```
   {
    "statuses": [
    {
        "created_at": "Sun Feb 25 18:11:01 +0000 2018",
        "id": 967824267948773377,
        "id_str": "967824267948773377",
        "text": "From pilot to astronaut, Robert H. Lawrence was the first African-American to be selected as an astronaut by any na… https://t.co/FjPEWnh804",
        "truncated": true,
        "entities": {
            "hashtags": [],
            "symbols": [],
            "user_mentions": [],
            "urls": [
                {
                    "url": "https://t.co/FjPEWnh804",
                    "expanded_url": "https://twitter.com/i/web/status/967824267948773377",
                    "display_url": "twitter.com/i/web/status/9…",
                    "indices": [
                        117,
                        140
                    ]
                }
            ]
        },
        "metadata": {
            "result_type": "popular",
            "iso_language_code": "en"
        },
        "source": "<a href='"https://www.sprinklr.com"' rel='"nofollow"'>Sprinklr</a>",
        "in_reply_to_status_id": null,
        "in_reply_to_status_id_str": null,
        "in_reply_to_user_id": null,
        "in_reply_to_user_id_str": null,
        "in_reply_to_screen_name": null,
        "user": {
            "id": 11348282,
            "id_str": "11348282",
            "name": "NASA",
            "screen_name": "NASA",
            "location": "",
            "description": "Explore the universe and discover our home planet with @NASA. We usually post in EST (UTC-5)",
            "url": "https://t.co/TcEE6NS8nD",
            "entities": {
                "url": {
                    "urls": [
                        {
                            "url": "https://t.co/TcEE6NS8nD",
                            "expanded_url": "http://www.nasa.gov",
                            "display_url": "nasa.gov",
                            "indices": [
                                0,
                                23
                            ]
                        }
                    ]
                },
                "description": {
                    "urls": []
                }
            },
            "protected": false,
            "followers_count": 28605561,
            "friends_count": 270,
            "listed_count": 90405,
            "created_at": "Wed Dec 19 20:20:32 +0000 2007",
            "favourites_count": 2960,
            "utc_offset": -18000,
            "time_zone": "Eastern Time (US & Canada)",
            "geo_enabled": false,
            "verified": true,
            "statuses_count": 50713,
            "lang": "en",
            "contributors_enabled": false,
            "is_translator": false,
            "is_translation_enabled": false,
            "profile_background_color": "000000",
            "profile_background_image_url": "http://pbs.twimg.com/profile_background_images/590922434682880000/3byPYvqe.jpg",
            "profile_background_image_url_https": "https://pbs.twimg.com/profile_background_images/590922434682880000/3byPYvqe.jpg",
            "profile_background_tile": false,
            "profile_image_url": "http://pbs.twimg.com/profile_images/188302352/nasalogo_twitter_normal.jpg",
            "profile_image_url_https": "https://pbs.twimg.com/profile_images/188302352/nasalogo_twitter_normal.jpg",
            "profile_banner_url": "https://pbs.twimg.com/profile_banners/11348282/1518798395",
            "profile_link_color": "205BA7",
            "profile_sidebar_border_color": "000000",
            "profile_sidebar_fill_color": "F3F2F2",
            "profile_text_color": "000000",
            "profile_use_background_image": true,
            "has_extended_profile": true,
            "default_profile": false,
            "default_profile_image": false,
            "following": null,
            "follow_request_sent": null,
            "notifications": null,
            "translator_type": "regular"
        },
        "geo": null,
        "coordinates": null,
        "place": null,
        "contributors": null,
        "is_quote_status": false,
        "retweet_count": 988,
        "favorite_count": 3875,
        "favorited": false,
        "retweeted": false,
        "possibly_sensitive": false,
        "lang": "en"
    }
   ],
   "search_metadata": {
    "completed_in": 0.057,
    "max_id": 0,
    "max_id_str": "0",
    "next_results": "?max_id=967574182522482687&q=nasa&include_entities=1&result_type=popular",
    "query": "nasa",
    "count": 3,
    "since_id": 0,
    "since_id_str": "0"
   }
   }
   ```

6. More Details [HERE](https://docs.tweepy.org/en/stable/api.html#search-tweets)

&nbsp;

##### 2. Instagram

![](https://i.ibb.co/kctSMsJ/insta.gif)

> Using own half baked insta scraper as the official api doesn't provide image and post caption without a 'Meta Approved' live app, that requires business verification and review from Meta.

- Limitation: Doesn't support infinite scroll.

- Scrapes the followings
  
  - Image or Video Thumbnail in JPG format
  
  - Post Caption containing Date, Hastags, URL to the image and filename. 
    
    ```json
    {
        "caption": "Hizbul Amin Ruposh on Instagram: May Allah Protect Devastating Flood Victims People In Sylhet Division In Bangladesh. Ameen. Video Credit : As Sunnah Foundation ♥ awarenessbangladeshvictimsreliefinbangladesh2022🤲",
        "hashtags": [
            "#prayforsylhet",
            "#floodbangladesh",
            "#sunamganj",
            "#flood",
            "#climatechange",
            "#climatechangeawareness",
            "#climatechangebangladesh",
            "#monsoonfloods",
            "#heavyrainfallflood",
            "#heavyrain",
            "#floodvictims",
            "#sylhetflood",
            "#floodrelief",
            "#assunnahfoundation",
            "#sylhet",
            "#floodinbangladesh",
            "#flood2022",
            "#prayforsylhet🤲\""
        ],
        "url": "https://scontent-ams4-1.cdninstagram.com/v/t51.29350-15/288906815_510557767526964_6140415943884138717_n.jpg?stp=dst-jpg_s640x640&_nc_cat=103&ccb=1-7&_nc_sid=8ae9d6&_nc_ohc=9A2q0RPkta4AX_ATjNi&_nc_ht=scontent-ams4-1.cdninstagram.com&oh=00_AT9T-9a-u3lb8CzF6P5XjI31icAXyAAYFIEoV_4vepZqSw&oe=62FC13B6",
        "filename": "288906815_510557767526964_6140415943884138717_n.jpg"
    }
    ```

- [Scraped Data Folder](https://drive.google.com/drive/folders/1x9D0aVCZF7oJSf1DhLPprH5z5wwMd00F?usp=sharing) [Accessible to Contributors]
  
  - Uncategorized data needs to be categorized

&nbsp;

##### 3. YouTube

![](https://i.ibb.co/q74h7cy/Screenshot-116.png)

> Extracted around 43k frames (1 frame per 2 seconds) as images from around 490 YouTube videos.

- Scraped the following metadata of the videos
  
  ```json
  {
      "video url": "https://www.youtube.com/watch?v=TcA7KBY3lIo",
      "video title": "নেত্রকোনায় ভয়াবহ হচ্ছে বন্যা! | Netrokona News | Flood News | BD Flood Update | Somoy TV",
      "hashtags": [
          "#Netrokona_Flood",
          "#Flood_News",
          "#BD_Flood_Update",
          "#SomoyNews",
          "#SomoyTV"
      ],
      "upload date": "2022-06-19 00:00:00",
      "channel title": "SOMOY TV"
  }
  ```

- [Scraped Videos with metadata](https://drive.google.com/drive/folders/1HmQmDvs4ZUQ7vCYwa7BdvOkCAu-fz2Ml?usp=sharing)

- [Extracted Frames](https://drive.google.com/drive/folders/1rdgDLeW-uJScXaV2pgz1vj7-2iY5KSkt?usp=sharing)

## &nbsp;

&nbsp;

## Contributors / Group Members

| <img src="https://avatars3.githubusercontent.com/u/26480837?s=460&u=146598a2935f43afa22df338549c6bd246ab37f5&v=4" title="" alt="" data-align="center"> | ![](https://avatars.githubusercontent.com/u/37307853?v=4) | ![](https://avatars.githubusercontent.com/u/72859164?v=4) | ![](https://avatars.githubusercontent.com/u/79776827?v=4) | ![](https://avatars.githubusercontent.com/u/68911875?v=4) | ![]()                            |
|:------------------------------------------------------------------------------------------------------------------------------------------------------:|:---------------------------------------------------------:|:---------------------------------------------------------:|:---------------------------------------------------------:|:---------------------------------------------------------:|:--------------------------------:|
| [Fahimul Hoque Shubho](https://github.com/FHShubho)                                                                                                    | [Abdullah Al Rafi](https://github.com/alrafiabdullah)     | [Parinda Rahman](https://github.com/parirahman)           | [Emon Sarker](https://github.com/emonsarkernsu)           | [Tahrima Ihsan](https://github.com/tahrima21)             | [Mohammad Tanvir Mahmud Habib]() |
