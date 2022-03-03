# Part II

In this part, we firstly did some data cleaning and categorized products using regex. Then we created functions for searching matched products and gave recommendation outfit combinations.

Input: a string of query

Output: printed sentences indicating searching results

## Overall query logic

* If the query is a product ID
 
  * In human domain experts' combinations: print out related experts' combos
  
  * Not In human domain experts' combinations: find the most similar product

* Vectorize query and dataset columns (Here we use name and description!)
  
  * One thing to be attentioned: we weighted name and description, since name matters more and too many noisy words in description

* Using cosine similarity to find the most similar product

  * Similarity should be bigger than a threshold

  * The most similar product should be a piece of clothing

* Return the most similar product and recommended outfit combinations


## Final Function

N-gram, TF-IDF and TF-IDF weighted word embedding all have good performances with our example queries. Considering the advancement of algorithm, we decided the TF-IDF weighted word embedding as our final function.
