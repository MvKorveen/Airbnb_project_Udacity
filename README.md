# Udacity course project: Airbnb Seattle data

This project uses the Seattle Airbnb data available on kaggle to investigate how large of an impact owner behaviour has on tenant demand

## Project description

### Questions to answer

These are the questions this repo seeks to answer:
* During which period of the year is items on airbnb in highest demand?
* Is there a higher demand over weekends?
* Does the user behaviour increase demand?
    - Does ratings for cleanliness and communication matter?
    - Do the customers premium high response rates?
    - Do a more comprehensive text description of the item affect demand?
    - What about the user details? Do the data imply that one should focus on a long personal description? 

### Data

The data used for this analysis is:
- Listings, including full descriptions and average review score
- Calendar, including listing id and the price and availability for that day

which can be downloaded at https://www.kaggle.com/datasets/airbnb/seattle/data

### CRISP-DM

The notebook in this repo covers steps 2-5 in the CRISP-DM methotdology. 

For step 1 I have used the variable descriptions provided in this kaggle post (https://www.kaggle.com/datasets/airbnb/seattle/discussion/273456) as well as the Data Wrangler function available in VS Code.

For a descriptive data presentation I have written a blog post on medium, which can be found in the link below: 
https://medium.com/@marcus.wik.84/why-less-is-more-on-airbnb-or-is-it-21c161c89754

### MAIN KPI

Since we are interested to know booking rate at the listings, we will use the variable availability to calculate the kpi variable "listing_booked".
Thus, tnstead of using "t" or "f" for available, we create the variable "listing_booked", taking on the value 1 if booked and 0 if not booked. If an item is unavailable (available==0), we make the assumption that it is booked.

*NOTE*: This is a simplification and a large assumption - further analysis and data clarification would be need for this assumption to be confirmed

## Prerequisites (With version controll)

* python = "^3.11"
* pandas = "^2.2.3"
* numpy = "^2.1.2"
* matplotlib = "^3.9.2"
* ipython = "^8.28.0"
* jupyter = "^1.1.1"
* holidays = "^0.59"
* seaborn = "^0.13.2"
* ipympl = "^0.9.4"
* scikit-learn = "^1.5.2"
* statsmodels = "^0.14.4"

## Usage

These two sets of data needs to be installed under the folder `airbnb_data` in the main folder in order to be gathered appropriatelly.

Following that, the notebook `airbnb_project.ipynb` can be run in full

## Main finding

1. During which period of the year is items on airbnb in highest demand?
    - Answer: Other than the closest period in the data, january, the largest demand is in july and august when 37% and 35% of the items are booked.

2. Is there a higher demand over weekends?
    - No, not in the overall dataset. However, since the most pre-booked dates seems to be during the summer months this could be that weekends and hollidays are not booked in advance at the same rate as summer hollidays.

3. Does the user behaviour increase demand?
    - 3.1. Does ratings for cleanliness and communication matter?
        - Where we actually have reviews, there is a larger chance that the object has been booked if the listing has scored a 10. The result is not linear, however.
        - The modelling for january in section 2.2.2. supports this result in terms of communication, but not for clenliness. 
        - Answer can be found in section 1.4.1.

    - 3.2. Do the customers premium high response rates?
        - To some extent, but it may be more of a matter of customers punishing users with less than 100% answering rate.
        - Answer can be found in section 1.4.3.
        - The model in section 2.2.2. supports that result.

    - 3.3. Do a more comprehensive text description of the item affect demand?
        - No, there is actually evidence of the opposite. The data points to there being a negative relationship between the number of words used leads to a higher bookings rate. LESS IS MORE!
        - Answer can be found in section 1.4.4.
        - This is supported by the modelling in section 2.2.2.

    - 3.4. What about the user details? Do the data imply that one should focus on a long personal description?
        - No, there is no evidence for such a relation.
        - Answer can be found in section 1.4.5.
        - No there is no linear result in section 2.2.2. to support this. Eventhough some dummies are significant they go up and down.

## Further recomendations
- additional controll variables should be added to try to increase the explanatory power of the model
- It is likelly that the assumptions made about an item not being available equals it being booked. Other datasets should be explored to do this.
    - Historical data would be preferable. Can we see which items where ACTUALLY on the market, but not booked at all?
- Do a word analysis on descriptions. What words are associated with a higher demand? 

## Acknowledgments
- A large share of the modeling approach as well the CRISP-DM methodology is gathered from the Udacity course Data Science.
- I have used the information gathered by the kaggle user Zacks Shen on the metadata for the Seattle dataset. This description can be found here: https://www.kaggle.com/datasets/airbnb/seattle/discussion/273456