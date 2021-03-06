# Universal Reddit Scraper
Universal Reddit scraper using the Reddit API ([PRAW](https://pypi.org/project/praw/)).

Written in Python.

**For a command-line interface version of this project, check out the [CLI version](https://github.com/JosephLai241/Universal-Reddit-Scraper-CLI/tree/master). This project is still under development, but expect a full working version soon!**

You will need to install the PRAW module in order for this program to work. `pip install praw` or `pip3 install praw` depending on your system. You will also need your own Reddit account and API credentials.

**NOTE:** PRAW currently only supports Python 2.7, 3.3, 3.4, 3.5, and 3.6. This project was written in Python 3 and tested with Python 3.6.

This is a universal Reddit scraper where you can manually specify subreddits to scrape, specify which category of posts to scrape for each subreddit, and how many results are returned. I have also added a search option where you can search for keyword(s) within a subreddit and the scraper will get all posts that are returned from the search.

Options for which category of posts to scrape for are as follows:
- Hot
- New
- Controversial
- Top
- Rising
- Search

*NOTE:* If you choose to search for something within a subreddit, all the results are returned and you will not be able to specify how many results are returned.

Once you configure the settings for the scrape, the program will write a .csv file to the same directory in which this scraper program is saved on your computer. The .csv file will include the Title, Score, ID, URL, Comment Count, Date Created, and the Text body of each post. 

The file names are formatted as such: "SUBREDDIT-POST_CATEGORY DATE.csv". If you have searched for a specific keyword in a subreddit, file names are formatted like so: "SUBREDDIT-Search-'KEYWORD' DATE.csv".

# How to get Reddit API Credentials

First, create your own Reddit account and then head over to [Reddit's apps page](https://old.reddit.com/prefs/apps).

Click "create app". Name your app and choose "script" for the type of app. In the redirect URL, type in "http://localhost:8080" since this is a personal use app. You can also add a description and an about URL. 

Once you create the app, you should see a string of 14 characters on the top left corner underneath "personal use script." That is your API ID. Further down you will see "secret" and a string of 27 characters; that is your API password. Save this information as it will be used in the program in order to use the Reddit API. You will also have to provide your app name, Reddit account username and password as well. 

This block of credentials is found on lines 15-19.

# Screenshots / Walkthrough

First, you will have to provide your own Reddit credentials in this block of code.

![Reddit credentials](https://github.com/JosephLai241/Universal-Reddit-Scraper/blob/assets/credentialblock.png)

**You have to provide valid credentials, otherwise the scraper will not work.**

When you initialize this program, you will be greeted with this screen.

![Start](https://github.com/JosephLai241/Universal-Reddit-Scraper/blob/assets/welcome.png)

You can choose to just scrape a single subreddit, or enter a list of subreddits separated by a space.

![Enter subs](https://github.com/JosephLai241/Universal-Reddit-Scraper/blob/assets/enter.png)

After entering the subreddit(s) you want to scrape, the program will check if the subreddit exists. It will separate the results from the check into a list of valid and invalid subreddits.

![Check subs](https://github.com/JosephLai241/Universal-Reddit-Scraper/blob/assets/checksubs.png)

You will then have the option to choose the post category within the subreddit (Hot, New, Controversial, Top, Rising, Search). After choosing the category, you will also have the option to choose how many results you would like to be returned. Again, this only applies if you do not choose the Search option.

![Settings 1](https://github.com/JosephLai241/Universal-Reddit-Scraper/blob/assets/settings1.png)

If you choose to search for keyword(s) within the subreddit, you will be greeted with these settings instead.

![Settings 2](https://github.com/JosephLai241/Universal-Reddit-Scraper/blob/assets/settings2.png)

After you have configured all settings for each subreddit, you will be greeted with the following screen which displays the settings you have configured.

![Settings overview](https://github.com/JosephLai241/Universal-Reddit-Scraper/blob/assets/overview.png)

When you confirm the settings, the program will write CSV files to the directory in which you saved the program and display the title of the post, the score (number of upvotes) of each post, post ID, post URL, comment count, date created, and additional text (body) of the post if there is any.

![Finish](https://github.com/JosephLai241/Universal-Reddit-Scraper/blob/assets/finish.png)

![CSVs created](https://github.com/JosephLai241/Universal-Reddit-Scraper/blob/assets/csvcreated.png)

# List of things I still have to add or change in this program
- As of now, users would have to start over if they decide they are not satisfied with their scrape settings. I might look into adding an option to either go back and redo the subreddit scrape settings or to completely start over. This way users will have options.

- ~~This program is optimized for use in the terminal, specifically for Linux-based distros. I will look into a way to neatly print out the scraped results into the terminal instead of creating CSV files for each scrape. Also considering adding a "Display scrape results in terminal / Create CSV file / Both? [T/C/B] " option.~~ I've decided to create a new repo for a command line optimized version of this project. The link to the CLI version of this project is located at the very top of this readme.

- I am still not exactly sure how to do PRAW exception handling, will have to look into that a bit more to catch invalid Reddit credentials, forbidden HTTP responses, etc.

- Considering adding an option where users can specify the data fields they would like in the CSV files instead of the current default fields.
