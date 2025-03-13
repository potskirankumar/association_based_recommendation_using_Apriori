# association_based_recommendation_using_Apriori
Association-based recommender using Apriori

Have you ever wondered about how online shopping sites recommend products?

When we are looking for some specific products like tripod for phones, case for phones, etc. on some sites, say Amazon. Again, when we open the Amazon application or site, we find tripod for phones with ring light, or phone cases recommended for you. These are recommendations based on users’ preferences.

Also, Netflix (as an example), when we watch say a movie like Extraction, an action and thriller movie, then after some time or when we access Netflix again, we will find something like Because You Watched “Extraction” tab (as an example) and some similar movies. That means, Netflix is using recommendation system to personalized users’ movies or shows.

So, recommendation system or simply we can call this as recommender is a system to recommend something based on users transactions or history.

As mentioned above, we need recommendation system or recommender to personalize users’ preferences. If we use a recommender on a shopping or ecommerce site or any other websites, we can recommend the products to any user or customer.

Let’s give another example here, on Facebook, there may be some tab or navigation that says People You May Know (I forget the actual words), this is another recommendation from Facebook. Also, when we watch a video like mukbang or some funny videos, Facebook will try to provide relevant contents. So, Facebook uses recommendation system.

In this article, the recommendation system here is built based on association rule. However, this system in this article is mostly based on data mining because the system focuses on pattern discovered in the users’ transactions (for future aspects, please read the Future aspects at the last part of this article). In this system, I manually add the items and some other data of customers. The customers are given with customer id. There are 100 customers and 100 transactions. Readers can use another dataset or some other data.

Recommendation system is important because it helps the users to discover products or services or contents that they might not have found and they might have interest in. The system uses users’ past behaviors and preferences which leads to users’ satisfaction, engagement, etc.

Note: Association rule in data mining and unsupervised machine learning can be used interchangeably and also related, but they are slightly different based on some context.

Association Rule
Association rule is a technique that can be used to find the relationships, patterns or associations between variables or data items of a large dataset. This technique is widely used in market basket analysis, fraud detection, recommendation system, etc.

The association rule is like “if-then” control statement. In a store, people use to buy bread, milk, cereal, vegetable, etc. if 80% of people buy milk, then there is a high chance of buying cereal (just an example). Also, if you or a user watched Extraction (movie, mentioned above), then there is a chance that you will watch Polar (another movie).

If a customer buys bread (antecedent), then he may buy milk (consequent). In generalization, association rule is like: X →Y, where X is the antecedent and Y is the consequent.

Itemset, this term is used very frequently, is a collection of one or more items in a transaction (transaction is one record of buying, like “if-then” part). So, with the above example, {bread}, {milk}, {bread, milk} are itemsets.

Frequent itemset: An itemset that appears in a significant number of transactions.

So, association rule is to identify how the occurrence of one itemset (or set of itemsets) is related to the occurrence of another in a transaction.

Some metrics are using to know the strength of association, they are Support, Confidence and Lift.

Support:

Support is a measure of how frequently an itemset occurs. Also, we can say, it is the proportion of transactions of containing antecedent (X) and consequent (Y) to total number of transactions.

Support = number of transactions containing X and Y / total number of transactions

From the above formula, we can say if value of support is high, it means the itemset is common.

Confidence:

Confidence gives the likelihood of occurrence of consequent when the antecedent has already occurred. It is given by diving the transactions containing X and Y by transactions containing only X.

Confidence = transactions containing X and Y / transactions containing only X.

Or Confidence = Support of X union Y / Support of X

Lift:

Lift is another metric in association rule which is used to measure the strength of an association between the if part and the then part. It evaluates whether the relationship between two itemset is stronger, weaker or same.

Lift = Support of X union Y / Support of X is multiplied by Support of Y.

Or Lift = Confidence / Support of Y.

Lift is greater than 1, means strong relationship and Y has more likelihood to occur. Lift is smaller than 1, means weak relationship and Y has less likelihood to occur. Lift is 1, means X and Y are not affecting each other.

Apriori Algorithm
Apriori algorithm was first introduced by Rakesh Agrawal and Ramakrishnan Srikant in 1994 in a paper called Fast Algorithms for Mining Association Rules [1] (I am adding [1] because I am going to use the ideas proposed in this paper, and saying I used this paper as a reference in explaining Apriori algorithm).

Apriori algorithm is a widely used data mining technique for finding frequent itemsets and generating association rules. It is also treated as an unsupervised machine learning algorithm. This algorithm acknowledges the prior knowledge of frequent itemsets that this algorithm uses in dataset.

Large itemset: itemsets with minimum support [1].

Algorithm (you can read the paper in the paper mentioned above)

Step 1:

Defining the minimum support value (minsup) and minimum confidence value (minconf) by users. The minsup and minconf are also called thresholds.

Step 2: Candidate Generation

Step 2a: Generate list of frequent 1-itemsets by scanning the data set and retaining those that meet minsup

Step 2b: Generate candidate itemsets by using frequent k-itemsets to generate candidate (k+1) itemsets by joining k itemsets.

Step 2c: Pruning: remove the itemsets that don’t meet the requirement that is minsup

Repeat step 2(s) until no more frequent itemset can be generated.

After all the frequent itemsets are identified, association rules are generated.

Step 3: Generating association rules: association rules are generated using A B, where A is subset of set of frequent itemsets and B, set of items in set of frequent itemsets but not in A.

Step 4: Evaluate using metrics like confidence and lift.

The algorithm above is from the original paper. And one important point here is the Apriori property that is if an itemset (non-empty) is frequent, then all its subsets must also be frequent.

#Building

I used mlxtend version 0.23.1, mlxtend is a python library which provides tools and utilities for data science. Using mlxtend, I used Apriori algorithm which is a predefined in the library.

I also used random to generate random customers ids and items.

Number of customers here in this system is 100.

Generating data for 100 customers and 100 transactions in which each transaction has 2 to 5 randomly selected items from the items list. Then, for random customer, there is item list assigned to the customer which is also random.

we create basket with idea that if a customer bought a particular item, the cell will contain 1, otherwise 0.

