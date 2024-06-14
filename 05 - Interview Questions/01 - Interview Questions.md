1. Kindly explain your project architecture?
2. Day to Day activity in office
3. What is the size of data you deal with on daily basis?
4. What is Repartition and Coalesce?
5. What optimisation techniques have you used in your project?
6. What is your role in your project?
7. What is the most challenging problem you have solved in your big data project?
8. Can you explain what happens internally when we submit a Spark job using Spark-Submit?
9. What is a catalyst optimiser?
10. What is the size of your Spark cluster and the configuration of each node?
11. How to tune a spark job? Please explain the techniques we can try.
12. What is Repartition and Coalesce?
13. What is Spark Context vs Spark Session?
14. Role in your current project
15. Difference between dataset & dataframe
16. Difference between broadcast variable & accumulator
17. What is broadcast Join?
18. Types of transformation and difference
19. What are operations of data frames
20. Explain Spark on Yarn Architecture
21. Why reduce is action & reduceByKey transformation
22. What is cache & persist in Spark
23. Difference between RDD & Dataframes
24. What are the challenges you face in spark?
25. How spark is better than Hive?
26. How to enforce schema on a data frame?
#### 27. What is difference between reduceByKey & groupByKey?
 - Spark groupByKey() and reduceByKey() are transformation operations on key-value RDDs, but they differ in how they combine the values corresponding to each key.

 Spark RDD groupByKey() is a transformation operation on a key-value RDD (Resilient Distributed Dataset) that groups the values corresponding to each key in the RDD. It returns a new RDD where each key is associated with a sequence of its corresponding values.

// Syntax of groupByKey()

def groupByKey(): RDD[(K, Iterable[V])]


Spark RDD reduceByKey() is another transformation operation on a key-value RDD (Resilient Distributed Dataset) that groups the values corresponding to each key in the RDD and then applies a reduction function to the values of each group. It returns a new RDD where each key is associated with a single reduced value.

// Syntax of reduceByKey()
def reduceByKey(func: (V, V) => V): RDD[(K, V)]

In Spark, both groupByKey and reduceByKey are wide-transformation operations on key-value RDDs resulting in data shuffling, but they differ in how they combine the values corresponding to each key.


#### 28. How do we submit jar files in Spark?
