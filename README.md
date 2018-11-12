# Vipul Chandoor

# Spark Project - Rubik's Cube

## About Me
This is Vipul Chandoor, Working as Graduate Assistant in Student Involvment Center for Student Activities Council. My major is Applied Computer Science in Northwest Missouri State University I will graduate in Spring 2019. 

I am using Rubik's cube wikipedia as my dataset.


## Objective 

I am calculating the Numbers of words repeated and the count of word is repeated, this is the main objecive of the project.

## Raw Data
The dataset contains about the Rubick's Cube. the source of dataset is Wikipedia. It explains what exaclty the rubick's cube is and when & who invented the rubick's cube. 

Source: [Rubick's Cube Wikipedia](https://en.wikipedia.org/wiki/Rubik%27s_Cube)

## Commands
1. Reading the dataset from the text file  
``` Scala 
    val text = sc.textFile("Datasets_Rubik'sCube.txt")
````

2. Spliting the dataset dividing with ",". 
``` Scala 
    val filtereddata = text.flatMap(_.split(" "))
````

3. Filtering the dataset with RegEx commands 
``` Scala 
    val filtereddata2 = filtereddata.filter(_.matches("^[a-zA-Z]*$"))
````

4. Filtering all the text and remaining will be only alphabets 
``` Scala 
    val filtereddata3 = filtereddata2.filter(_.length >= 1)
````

5. Making it into Tuple
``` Scala 
    var mapout = filtereddata3.map((_,1))
````

6. Reducer
``` Scala 
    val reducerout = mapout.reduceByKey(_ + _)
````

7. making key to value  and value to key
``` Scala 
    var sortedout = reducerout.map { case (key,value) => (value,key) }
````
8. Sorting the output
``` Scala 
    sortedout = sortedout.sortByKey(false)
````

9. Taking only 1st 20 words
``` Scala 
    sortedout.take(20)
````

## Results 

My dataset is about Rubik's Cube. 
there are many words which are repeated many times. Word "THE" is used 42 times in the whole dataset, Word "AND" is used for 22 times and many other words for mant times. 

| Word   | Count |
|--------|-------|
| the    | 42    |
| and    | 22    |
| of     | 21    |
| in     | 20    |
| to     | 16    |
| Cube   | 14    |
| was    | 11    |
| is     | 7     |
| puzzle | 7     |
| that   | 7     |
| a      | 7     |
| by     | 6     |
| Magic  | 6     |
| it     | 5     |
| be     | 5     |
| Toy    | 4     |
| its    | 4     |
| first  | 4     |
| his    | 4     |
| each   | 4     |

![Screenshot](https://raw.githubusercontent.com/chandoorvipul/Spark_Project_Chandoor/blob/master/Images/Screenshot.PNG)
 
Link to the Hosted Site : [https://chandoorvipul.github.io/Spark_Project_Chandoor/.](https://chandoorvipul.github.io/Spark_Project_Chandoor/.)
