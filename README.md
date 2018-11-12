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
1.
``` Scala 
     val text = sc.textFile("Datasets_Rubik'sCube.txt")
````
2.
``` Scala 
    val text = sc.textFile("Datasets_Rubik'sCube.txt")
````
3.
``` Scala 
    val filtereddata = text.flatMap(_.split(" "))

````
4.
``` Scala 
    val filtereddata2 = filtereddata.filter(_.matches("^[a-zA-Z]*$"))
````
5.
``` Scala 
    val filtereddata3 = filtereddata2.filter(_.length >= 1)
````
6.
``` Scala 
    var mapout = filtereddata3.map((_,1))
````
7.
``` Scala 
    val reducerout = mapout.reduceByKey(_ + _)
````
8.
``` Scala 
    var sortedout = reducerout.map { case (key,value) => (value,key) }
````
9.
``` Scala 
    sortedout = sortedout.sortByKey(false)
````
10.
``` Scala 
    sortedout.take(20)
````

## Results 

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

![Screen Shot](https://github.com/chandoorvipul/Spark_Project_Chandoor/blob/master/Images/Screenshot.PNG)
 
 [Link to the Hosted Site](https://chandoorvipul.github.io/Spark_Project_Chandoor/.) 
