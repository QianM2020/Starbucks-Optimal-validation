Portfolio Exercise: Starbucks

# Background Information
  The dataset you will be provided in this portfolio exercise was originally used
  as a take-home assignment provided by Starbucks for their job candidates. In
  the experiment simulated by the data,
  an advertising promotion was tested to see if it would bring more customers to
  purchase a specific product priced at $10. Since it costs the company 0.15 to
  send out each promotion, it would be best to limit that promotion only to those
  that are most receptive to the promotion.

# Data
  The data for this exercise consists of about 120,000 data points split in a 2:1
  ratio among training and test files. Each data point includes one column
  indicating whether or not an individual was sent a promotion for the product,
  and one column indicating whether or not that individual eventually purchased
  that product. Each individual also has seven additional features associated
  with them, which are provided abstractly as V1-V7.

# Optimization Strategy
  The task is to use the training data to understand what patterns in V1-V7 to
  indicate that a promotion should be provided to a user. Specifically, the goal
  is to maximize the following metrics:
  * Incremental Response Rate (IRR)
      𝐼𝑅𝑅=𝑝𝑢𝑟𝑐ℎ𝑡𝑟𝑒𝑎𝑡/𝑐𝑢𝑠𝑡𝑡𝑟𝑒𝑎𝑡−𝑝𝑢𝑟𝑐ℎ𝑐𝑡𝑟𝑙/𝑐𝑢𝑠𝑡𝑐𝑡𝑟𝑙
      IRR depicts how many more customers purchased the product with the promotion,
      as compared to if they didn't receive the promotion. Mathematically, it's the
      ratio of the number of purchasers in the promotion group to the total number
      of customers in the purchasers group (treatment) minus the ratio of the number
      of purchasers in the non-promotional group to the total number of customers
      in the non-promotional group (control).
  * Net Incremental Revenue (NIR)
      𝑁𝐼𝑅=(10⋅𝑝𝑢𝑟𝑐ℎ𝑡𝑟𝑒𝑎𝑡−0.15⋅𝑐𝑢𝑠𝑡𝑡𝑟𝑒𝑎𝑡)−10⋅𝑝𝑢𝑟𝑐ℎ𝑐𝑡𝑟𝑙
      NIR depicts how much is made (or lost) by sending out the promotion.
      Mathematically, this is 10 times the total number of purchasers that received
      the promotion minus 0.15 times the number of promotions sent out, minus 10
      times the number of purchasers who were not given the promotion.

#  Test Strategy
      When have an optimization strategy, use the promotion_strategy function to get
      the test_results function.
      There are four possible outcomes:
                                  Actual
                        Predicted	Yes	No
                        Yes	       I	II
                        No 	     	III	IV
      Comparing quadrant I to II then gives an idea of how well the promotion strategy 
      will work in the future.

# The classifier used in the project to train the model is 'SVM'. I set the parameters = {
        'clf__C': (1,10,100),
        'clf__gamma': (1,10,100), 
        'clf__kernel': ('linear','rbf','poly','sigmoid'),
    }
and used GridSearchCV to find the best parameters.
