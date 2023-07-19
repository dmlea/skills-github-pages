---
title: "Using Data Science to Eat Happily Across Europe"
date: 2023-07-19
---
![image](https://github.com/dmlea/skills-github-pages/assets/59482493/70243219-0e21-4b56-92a0-015eb98e043d)


Are you thinking of traveling to Europe, and are you enough of a "foodie" to plan your trip around being able to eat well wherever you go?

Or did you enjoy your last European trip (and food) so much that you dream of moving there to open a restaurant?

Well, data science can help!

## Introduction

This post will describe some insights (nothing too sophisticated - I'm a data science rookie) derived from a publicly available Kaggle dataset of Tripadvisor ratings for European restaurants: https://www.kaggle.com/datasets/damienbeneschi/krakow-ta-restaurans-data-raw

My goal was to answer three questions:

1) Which cities have the highest rated low and moderately priced restaurants?

2) Regardless of price range, which cities have the highest average ratings for Mediterranean and Vegetarian Friendly restaurants?

3) Which cities would be good candidates for opening an American restaurant?

(A couple of these questions are rather specific, but it should be easy for you to imagine using the dataset to answer other similar questions.)

## Data preprocessing

The Kaggle dataset covers over 125,000 restaurants (one per row) in 31 European cities and has 11 columns.  I began by pruning some columns and rows to make the work more efficient. I won't bore you with the details of the columns I pruned, but I kept these six:

1) Name of restaurant
   
2) City
 
3) Cuisine style
 
4) Average customer rating (1 to 5 stars, in increments of 0.5)
 
5) Price range (Low, Moderate, High)
 
6) Number of reviews

Regarding rows, there were about 9000 which had no value for customer rating.  I planned to use customer rating as the quality metric for drawing conclusions, so it made no sense to keep those rows. After I deleted them, I had about 116,000. 

There were an additional ~35,000 rows in which the number of reviews was fewer than 10.  To me, a single-digit number of reviews seemed like too small a sample size to provide a reliable assessment, so I deleted those rows as well, leaving a little over 80,000 restaurants (still a pretty large number!) for my analysis.

![image](https://github.com/dmlea/skills-github-pages/assets/59482493/f1a68092-3b95-4b57-a590-f50066d1c96f)

I also wanted to make sure that my row deletions had left a reasonable number of restaurants for each city, so I generated the table below, which also gives you a chance to see which 31 cities are represented.  I was pleased to see that I had still had well over 200 restaurants for each city:

![image](https://github.com/dmlea/skills-github-pages/assets/59482493/3f30c689-efb6-4fdf-845e-1ba88879688b)

Then I was ready to start working on answering my three questions.

## 1) Which cities have the highest rated low and moderately priced restaurants?

To make sure that the **Low** and **Moderate** ranges both had a sufficient number of restaurants for analysis, I made the plot below. (The "nan" category captures restaurants with no price range specified in the dataset. I didn't delete them, because I wanted to be able to use them for questions 2 & 3.)  **Moderate** is by far the largest group, but **Low** has ~15000 restaurants, sufficent for comparing average ratings across cities.

![image](https://github.com/dmlea/skills-github-pages/assets/59482493/4247e954-10eb-492f-931a-9b58541eef4c)

I then proceeded to make the next two plots (recall that 5 is the highest possible rating):

![image](https://github.com/dmlea/skills-github-pages/assets/59482493/b0c10109-4efb-4e3e-998e-2370af1fedf4)  ![image](https://github.com/dmlea/skills-github-pages/assets/59482493/502e234f-eac2-4a67-a9d2-efea3dde5890)

Athens, Krakow, Rome, Berlin, Amsterdam and Ljubljana look like the big winners here. They're the 6 highest rated cities for low priced restaurants, and among the top 8 for moderately priced ones.  If you want to eat well on a limited budget, you should prioritize including a couple of them.  (They're fairly spread out geographically, so your limited budget may not let you visit all 6. 🙂)

## 2) Regardless of price range, which cities have the highest average ratings for Mediterranean and Vegetarian Friendly restaurants?

At this point, I did a little more row pruning. I knew that for the rest of my analysis, I was going to analyze ratings of particular cuisine styles, so I deleted about 9000 rows which had no value for cuisine style. That left a little over 70,000 restaurants:

![image](https://github.com/dmlea/skills-github-pages/assets/59482493/864ba5b9-3029-4626-957c-1bf599178547)

Then I made separate rating plots for the Mediterranean and Vegetarian Friendly cuisine styles:

![image](https://github.com/dmlea/skills-github-pages/assets/59482493/d6322aeb-cd14-4bc5-8887-2c5cb2a9fbaf)  ![image](https://github.com/dmlea/skills-github-pages/assets/59482493/6f910f99-a213-4d0e-91c1-4d0cb1415732)

A rather surprising result here is that the four highest scorers in the first plot (Edinburgh, Dublin, Krakow, Prague) are nowhere near the Mediterranean!  I suspect that those ratings are influenced somewhat by customer expectations; i.e., many customers probably (perhaps subconsciously) hold Mediterranean-adjacent Mediterranean restaurants to a higher standard.  To me, the message is that Mediterranean restaurants in Northern and Central Europe can be very good, even if they aren't actually *better* than ones in Southern Europe.

As for the Vegetarian Friendly plot, it doesn't have a strong geographic theme.  But we can make one significant observation: Prague is the only city in the Top 4 in both the Mediterranean and Vegetarian Friendly plots.  If those are among your favorite cuisines, Prague should definitely be on your itinerary. (Famous for its beautiful architecture too!)

## 3) Which cities would be good candidates for opening an American restaurant?

Now we're going to think outside the box a little, and imagine helping American cooks looking to move to Europe and open restaurants specializing in the cuisine of their native land.  Here I took the opposite approach compared to Questions 1 and 2: I looked for the cities with the *smallest* fraction of American restaurants with an average rating of 4.5 or 5 stars. A new high-quality American restaurant there would have less competition and would more likely succeed.

Our answer comes from the plot below, and this time we need to focus on the *right* side of it (lowest values): 

![image](https://github.com/dmlea/skills-github-pages/assets/59482493/25f68d01-62df-4546-831c-7e374e143d09)

The best candidates are Helsinki, Zurich, Oslo, Milan, Stockholm. In those cities, less than 20% of American restaurants have a 4.5 or 5 rating. Noting three of those cities in particular, it appears that a talented American cook who doesn't mind the thought of long, cold Scandinavian winters would have a good chance at succeeding with a new restaurant there. 

## Conclusion

We've learned that by applying a little data preprocessing and logical reasoning to a publicly available dataset, we can use data science to answer important questions for preparing a European journey.  Your interests (food or otherwise) may not align with mine, but once you have a little data science background, you'll be ready to use the restaurant dataset (or ones for museums, theatres, etc.) for similar analysis.  Happy travels!
