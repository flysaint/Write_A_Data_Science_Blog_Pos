
## 1 商业理解（business understanding）
Problem I want to solve:
I just split Seatte houses into two parts by the price.The high price house's price is more than median price (119).The low price house's price is less than median price(119).
then I want to find out that:
**Question1**. What's the differece between high price houses and low price houses.
**Question2**. If you are a low/high house host,what should you do to improve the review score value?
**Question3**. Question3 If we are the house hosts,and if we want to be a superhost,what should we do while we are high price house host or low price house host?<br/>


## 2. 数据理解（data understanding）
### 2.1 Load the data


### 2.2 Preview the data
The data are mainly divided into the following aspects:
**Host information**
host_response_time,host_response_rate,host_is_superhost,host_listings_count,host_total_listings_count
**House hardware information**
neighbourhood_group_cleansed,zipcode,property_type,room_type,accommodates,bathrooms,bedrooms
**House other information**
price,security_deposit,cleaning_fee,minimum_nights,maximum_nights,availability_365,instant_bookable,cancellation_policy
**House scrore information** review_scores_rating,review_scores_rating,review_scores_accuracy,review_scores_cleanliness,review_scores_checkin,review_scores_communication,review_scores_location,review_scores_value




## 3 数据准备（data preparation）- Data clean
### 3.1 First process. 
1**Singe value process.** If a feature only have one unque value,then it have no value for our analysis. And at last,we delete scrape_id,experiences_offered,and so on . <br/>

2 **Null value process.** If a feature only have a miss rate more than 0.85,then it have no value for our analysis. And at last,we delete thumbnail_url,xl_picture_url,and so on . </br>

3 **Big proportion process.** If a feature only have one value rate more than 0.9,then it have litte value for our analysis. And at last,we delete host_has_profile_pic,street,and so on. <br/>



### 3.2 Choose  variables to continue observe 

**预测各个价格区间段内，对用户多次订购影响最大的因素，从以下几个方面选择** <br/>
After the first process step,we select features to watch in the following ways:

1. Host information. host_response_time,host_response_rate,host_is_superhost,host_listings_count,host_total_listings_count
2. House hardware information. neighbourhood_group_cleansed,zipcode,property_type,room_type,accommodates,bathrooms,bedrooms
3. House other information. price,security_deposit,cleaning_fee,minimum_nights,maximum_nights,availability_365,instant_bookable,cancellation_policy
4. House scrore information. review_scores_rating,review_scores_rating,review_scores_accuracy,review_scores_cleanliness,review_scores_checkin,review_scores_communication,review_scores_location,review_scores_value




### 3.3 Variable transformation（针对性处理)
1) **host_response_time.** The feature 'host_response_time' can means if a host'respone time is faster ,then we can say the host have a better sevice.so I process it to be a sequence variable.The varible is bigger ,then the sevice is better. <br/>
2) **host_response_rate.** the host_response_rate should be a numerical value,so I trim the "%" from the value. <br/>
3) **price,security_deposit,cleaning_fee.**Those two col are money value,so I trim '$' from them.


### 3.4 Numerical variable processing(数值变量处理。)
We select num_features to process:<br/>
1) If the miss rate is more than 0.6 then delete this variable,and add a col to indicate wheather the value is null.<br/>
2) If the miss rate is less than 0.6,then fill the miss value with random value from the not miss value.</br>


### 3.5 Categorical variable processing(分类变量处理)

We process the categorical varibles in the following ways:<br/>
1) If miss rate is more than 0.8 then delete this variable,else fill then miss value with '-1'. <br/>
2) One-hot encoding. <br/>

### 3.6 reveiw again(再次遍历处理) <br/>
after we process features by the ways above all,we should process the single value ,the big proportion again.

## 4.EDA(数据探索)
I want to find out that :<br/>
1) what's the difference between the high price house and the low price house. <br/>
2) If we are the host,when our houses is high/low price house,what should we do to improve the review score? <br/>
3) If the host is a superhost,what's difference between high/low price houses.

We select the features like beds,bathrooms,accommodates and so on to watch the difference between high/low price houses.



## 5. Build Module(建立模型)

**Question2 If you are a low/high house host,what should you do to improve the review score value?**
**Conclusion**
1. From the pictures above,we can see both high price houses' users and low price houses' users care about 
review_scores_cleanliness,review_scores_cleanliness,cleaning_fee,security_deposit,maximum_nights,minimum_nights.accommodates. <br/>
2. If you are a low price houses's host,you should try to be a superhost at first,and then maybe you should not make your the houses cancellation policy to be a strict grace period. <br/>
3. If you are a high price houses' host , more care about beds,and bedrooms,and wheather the house is a Apartment.




**Question3 If we are the house hosts,If we want to be a superhost,what should we do while we are high price house host or low price house host?**
**conclusion**

From the figtures above,we can see that both of low/high price house's hosts are been influenced by cleaning_fee,maximum_nights,review_scores_value,secutity_deposit,review_scores_cleanliness,host_reponse_rate_flag,host_reponse_time_flag.
So if we want to be superhost,there have not much different between low price houses and high price houses 

