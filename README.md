# Automatic Deploying with Jenkins on an AWS EC2 instance (Includes GitHub + Docker + Git)
<p> <br/ >

## To deploying model we try to best model accuracy. And after tuning some of the parameters and adding some more data, you expect had better accuracy than the previous model built. That' s mean you plan to deploy this model and you have to go through the trouble of building, testing and deploying the model to production again which is a lot of work.
You can tedious to manually run tests weekly, or even daily, which is where a CI/CD or Continuous Integration/ Continuous Deployment Pipeline like Jenkins comes in. Jenkins allows us to automatically run tests weekly, daily, hourly, or even on commit to a repository. 
In this article, I will show you how we can use a powerful tool called Jenkins to automate this process.

![Jenkins_DataSci](https://user-images.githubusercontent.com/91700155/171888179-281f8d18-7585-40fb-820c-19a2598a8524.png)

  
## What is Jenkins?
In addition to automating other routine development tasks, Jenkins provides a simple way to set up a continuous integration or continuous delivery (CI/CD) environment for virtually any language and source code repository combination that uses pipelines. While Jenkins doesn't eliminate the need to create scripts for individual steps, it does offer a faster and more robust way to integrate your entire chain of build, test, and deployment tools than you can easily build yourself.
  
## For example, you can set up Jenkins to automatically detect code commit in a repository and automatically trigger commands either creating a Flask application using Docker building a Docker image from a Dockerfile, running unit tests or push an image to a container registry or deploy it to the production server without manually doing anything.
Let's look basic concept we need to know in order to perform some automation in our project. 


## Jenkins features
Jenkins has some features that really sell it as a CI/CD tool. These are some of them:

- Plug-ins
- Easy to set up
- Supports most environments
- Open-source
- Easy distribution
  
It is evident from the above points that Jenkins has a very high demand globally. Before we dive into Jenkins it is important to know what is Continuous Integration and why it was introduced.
  
## Before the practical side, there are some important terms need to know.
  
## Jenkins Job  
Jobs are the heart of Jenkins' build process. In Jenkins, a job can be thought of as a specific task to achieve a necessary purpose. We can also create and build these jobs to test our app or project. Jenkins provides the following types of build jobs that a user can create based on need.
Creating Job is very easy in Jenkins but in a software environment, you may not build a single job but instead, you’ll be doing what is referred to as a pipeline.
  
  
## Jenkins Pipeline
  
  
## Steps
### Installation 
This is part 2 of my series on deploying Jenkins to create an efficient CI/CD Pipeline. In part one, I covered installing and launching Jenkins on a AWS EC2 instance. You can find part one link below:

---------
  
  

  
  
  
https://github.com/sedaatalay/Running-Jupyter-Notebook-on-AWS-EC2-Server
 
<p> <br/ >
 
## Creating an sample in Jupyter Notebook
  
### Simply import Apache Spark via 
  
```console
import findspark
findspark.init()
import pyspark
from pyspark import SparkConf, SparkContext
from pyspark.sql import SparkSession
from pyspark.sql.functions import *
from random import randint, choice
import string  
```
<img width="739" alt="Ekran Resmi 2022-05-24 21 34 06" src="https://user-images.githubusercontent.com/91700155/170107919-03638278-6085-43ed-959b-4ec1ba95901d.png">
  
### Spark Context 
  
#### To run Spark, we need to initialize a Spark context. A Spark context is the entry point to Spark that is needed to deal. We can initialize one simply as follows:
  
```console
conf = SparkConf().setMaster("local").setAppName("app")
sc = SparkContext.getOrCreate()
spark = SparkSession.builder.getOrCreate()
```
<img width="735" alt="Ekran Resmi 2022-05-24 21 34 13" src="https://user-images.githubusercontent.com/91700155/170107977-be7296d6-952b-4cd8-a6a7-167443187e58.png">

  
### Create random generated samples (has 50 dimensions) 
```console
def randCol():
  return rand(seed=randint(0,1000)).alias(choice(string.ascii_letters))
```
<img width="732" alt="Ekran Resmi 2022-05-24 21 34 58" src="https://user-images.githubusercontent.com/91700155/170108080-238809e2-0841-4269-9c8d-c97c67e73374.png">  
  
#### or
```console
import pandas as pd
import
numpy as np
df= pd.DataFrame np.random.randint (0,100,size=(1000000, 51)), np.arange (
df
``` 
```console
df.to_csv('data.csv',index =None)
```
<img width="575" alt="Ekran Resmi 2022-05-24 21 32 50" src="https://user-images.githubusercontent.com/91700155/170107420-08c696d1-4219-4646-a063-c4e37ac51a5c.png">  
  
### SQLContext
  
#### SqlContext is the entry point to SparkSQL which is a Spark module for structured data processing. Once SQLContext is initialised, the user can then use it in order to perform various “sql-like” operations over Datasets and Dataframes.
```console
df = sqlContext.range(0, 50).select("id", randCol(),randCol(),randCol())
df.show(5)
``` 
<img width="729" alt="Ekran Resmi 2022-05-24 21 37 30 2" src="https://user-images.githubusercontent.com/91700155/170108441-6f6763ea-5f42-4d53-adf4-c75becb88b55.png">
<img width="727" alt="Ekran Resmi 2022-05-24 21 37 30" src="https://user-images.githubusercontent.com/91700155/170108427-83997cd8-f505-414d-af91-967c29e2d410.png">
  
  
### Mean, Min, Max
  
#### Mean
```console
df.select([mean(df.schema.names[1]), mean(df.schema.names[2]), mean(df.schema.names[3])]).show()
``` 
<img width="734" alt="Ekran Resmi 2022-05-24 21 39 21" src="https://user-images.githubusercontent.com/91700155/170108693-5a24189a-e3d7-40e0-a0f9-6507bcb23c5d.png">

#### Min
```console
df.select([min(df.schema.names[1]), min(df.schema.names[2]), min(df.schema.names[3])]).show()
``` 
<img width="733" alt="Ekran Resmi 2022-05-24 21 39 30" src="https://user-images.githubusercontent.com/91700155/170108728-85a594dc-d03b-49d7-9410-17e8c4d10ab0.png">

#### Max
```console
df.select([max(df.schema.names[1]), max(df.schema.names[2]), max(df.schema.names[3])]).show()
``` 
<img width="731" alt="Ekran Resmi 2022-05-24 21 39 56" src="https://user-images.githubusercontent.com/91700155/170108746-67059f6e-b422-4b8a-b307-a13676e65080.png">

  
### Variance, Covariance
  
#### Variance
```console
df.agg({df.schema.names[1]: 'variance'}).collect()
``` 
<img width="734" alt="Ekran Resmi 2022-05-24 21 41 18" src="https://user-images.githubusercontent.com/91700155/170109152-ba789676-3874-4f13-882d-58d23d91a6b9.png">
  
#### Covariance
```console
df.stat.cov(df.schema.names[1], df.schema.names[2])
``` 
<img width="731" alt="Ekran Resmi 2022-05-24 21 41 26" src="https://user-images.githubusercontent.com/91700155/170109186-1861e197-617a-4ddc-ad57-00484cc7709d.png">
  
### FreqItems  
```console
df.stat.freqItems(df.schema.names, 0.3).collect()
```
<img width="734" alt="Ekran Resmi 2022-05-24 21 41 33" src="https://user-images.githubusercontent.com/91700155/170109238-4c1eeeab-ffaf-4442-a305-2b077ac70552.png">
  
### Math Functions  
```console
df.select(df.schema.names[1],
  (pow(sin(df[df.schema.names[1]]), 4) * sin(df[df.schema.names[1]])).alias("Sinus Equeation"),
  toDegrees(df.schema.names[1]),).show()
```   
<img width="729" alt="Ekran Resmi 2022-05-24 21 41 40" src="https://user-images.githubusercontent.com/91700155/170109297-3fa28937-8c38-4987-8b95-ca087954bff0.png">
<img width="729" alt="Ekran Resmi 2022-05-24 21 54 13" src="https://user-images.githubusercontent.com/91700155/170111316-cdcd08aa-ee7b-4ca5-9c39-4baeb4f12ff0.png">

### ColStats  
```console
df.summary().show()
```   
<img width="733" alt="Ekran Resmi 2022-05-24 21 42 05" src="https://user-images.githubusercontent.com/91700155/170109437-8c43356f-1115-4edc-b9ed-5ee2c0ff10c6.png">
  
### Describe 
```console
df.describe().show()
```    
<img width="734" alt="Ekran Resmi 2022-05-24 21 41 59" src="https://user-images.githubusercontent.com/91700155/170109489-4bc22f06-3b1d-4694-93fa-1601103d9408.png">

### Crosstab 
```console
companies = ["IBM", "Google", "Huawei","Netflix","Meta","Tesla"]
positions = ["Software Engineer", "Big Data Analyst", "MLOps Specialist", "Data Scientist", "Machine Learning Engineer"
compy_df = sqlContext.createDataFrame([(companies[i % len(companies)], positions[i % len(positions)]) for i in range
compy_df.show()
```   
<img width="736" alt="Ekran Resmi 2022-05-24 21 42 15" src="https://user-images.githubusercontent.com/91700155/170109565-67c9bd5b-35d1-4465-96f4-3f528f237423.png">
<img width="736" alt="Ekran Resmi 2022-05-24 21 56 57" src="https://user-images.githubusercontent.com/91700155/170111671-898e9a83-5218-44c4-938c-c9bfd00640a8.png">
 
```console
compy_df.stat.crosstab("Companies", "Positions").show()
```      
<img width="734" alt="Ekran Resmi 2022-05-24 21 42 33" src="https://user-images.githubusercontent.com/91700155/170109666-3bd1ccc9-0e33-4c18-b8bd-6d463df9fe68.png">
  
  
#### Thank you :) 
<p>  <br /><br />
</p>

### Seda Atalay
