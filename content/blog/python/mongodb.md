---
title: Python and Mongodb
date: 2021-09-12 00:00:00 +0300
description: #
img: ./workflow.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [python,mongodb] # add tag
---
Change examples my own dB

Working with python and mongodb on windows desktop.

* Create a docker hosted MongoDB database
* Install PyMongo, the Python Driver
* Connect to MongoDB
* Explore MongoDB Collections and Documents
* Perform basic Create, Retrieve, Update and Delete (CRUD) operations using PyMongo
* Build imports for CSV files  to mongo collections.

## PyMongo

PyMongo is the official Python driver for MongoDB
see [1](#1)

### Installation

python -m pip install pymongo

### Connection to database

```py
from pymongo import MongoClient
from pprint import pprint
# connect to MongoDB, change the << MONGODB URL >> to reflect your own connection string
client = MongoClient(<<MONGODB URL>>)
db=client.admin
# Issue the serverStatus command and print the results
serverStatusResult=db.command("serverStatus")
pprint(serverStatusResult)
```

### Basic CRUD operations using PyMongo

```py
from pymongo import MongoClient
client = MongoClient('<<MongoDB URL>>’)
# create database
db = client.business
#Step 2: Create sample data
names = ['Kitchen','Animal','State', 'Tastey', 'Big','City','Fish', 'Pizza','Goat', 'Salty','Sandwich','Lazy', 'Fun']
company_type = ['LLC','Inc','Company','Corporation']
company_cuisine = ['Pizza', 'Bar Food', 'Fast Food', 'Italian', 'Mexican', 'American', 'Sushi Bar', 'Vegetarian']
for x in range(1, 501):
    business = {
        'name' : names[randint(0, (len(names)-1))] + ' ' + names[randint(0, (len(names)-1))]  + ' ' + company_type[randint(0, (len(company_type)-1))],
        'rating' : randint(1, 5),
        'cuisine' : company_cuisine[randint(0, (len(company_cuisine)-1))]
    }
    #Step 3: Insert business object directly into MongoDB via insert_one
    result=db.reviews.insert_one(business)
    #Step 4: Print to the console the ObjectID of the new document
    print('Created {0} of 500 as {1}'.format(x,result.inserted_id))
#Step 5: Tell us that you are done
print('finished creating 500 business reviews')
```

### Find operations

```py
fivestar = db.reviews.find_one({'rating': 5})
print(fivestar)
#
fivestarcount = db.reviews.find({'rating': 5}).count()
print(fivestarcount)

```

## Aggreation pipeline

MongoDB aggregation pipeline :

```py
from pymongo import MongoClient
# Connect to the MongoDB, change the connection string per your MongoDB environment
client = MongoClient(port=27017)
# Set the db object to point to the business database
db=client.business
# Showcasing the count() method of find, count the total number of 5 ratings
print('The number of 5 star reviews:')
fivestarcount = db.reviews.find({'rating': 5}).count()
print(fivestarcount)
# Now let's use the aggregation framework to sum the occurrence of each rating across the entire data set
print('\nThe sum of each rating occurance across all data grouped by rating ')
stargroup=db.reviews.aggregate(
# The Aggregation Pipeline is defined as an array of different operations
[
# The first stage in this pipe is to group data
{ '$group':
    { '_id': "$rating",
     "count" :
                 { '$sum' :1 }
    }
},
# The second stage in this pipe is to sort the data
{"$sort":  { "_id":1}
}
# Close the array with the ] tag
] )
# Print the result
for group in stargroup:
    print(group)
```

### Update operation with PyMongo

```py
from pymongo import MongoClient
#include pprint for readabillity of the
from pprint import pprint

#change the MongoClient connection string to your MongoDB database instance
client = MongoClient(port=27020)
db=client.business

ASingleReview = db.reviews.find_one({})
print('A sample document:')
pprint(ASingleReview)

result = db.reviews.update_one({'_id' : ASingleReview.get('_id') }, {'$inc': {'likes': 1}})
print('Number of documents modified : ' + str(result.modified_count))

UpdatedDocument = db.reviews.find_one({'_id':ASingleReview.get('_id')})
print('The updated document:')
pprint(UpdatedDocument)
```

#### Deleting documents

 the delete_one and delete_many command takes a query that matches the document to delete as the first parameter.

```py
result = db.restaurants.delete_many({“category”: “Bar Food“})
```

## Resources

<a name="1"></a>[PyMongo drivers](https://docs.mongodb.com/drivers/python)
<a name="2"></a>[Mongo course](https://university.mongodb.com/courses/M101P/about)