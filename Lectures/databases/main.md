# Databases and Docker intro

Today we're going to continue talking about databases and how to integrate them into your projects. Databases offer centralized persistent storage with some fantastic garuntees about data consistency, availability, and/or partition tolerance (generally you only get two out of the three, unless you're [Google Spanner](https://cloud.google.com/spanner/?utm_source=google&utm_medium=cpc&utm_campaign=na-US-all-en-dr-bkws-all-all-trial-e-dr-1003905&utm_content=text-ad-none-any-DEV_c-CRE_201438283354-ADGP_Hybrid%20%7C%20AW%20SEM%20%7C%20BKWS%20%7C%20Multi%20~%20Google%20Spanner-KWID_43700021846306996-kwd-343702663564&utm_term=KW_google%20spanner-ST_google%20spanner&gclid=EAIaIQobChMIjdL358Lf2QIVQUOGCh3zAQVtEAAYASAAEgJEQPD_BwE&dclid=CI3U6ujC39kCFQtmwQodrQMLNw)). 

## MongoDB
MongoDB is a non-relational "NoSQL" database that is essentially an object store -- it lets you build structured objects and put them into storage with easy queries for retrieval later. Generally MongoDB is a __schemaless__ database (unlike SQL databases), which means you generally do not have to specify a data structure schema for objects before inserting them into collections. This isn't great for programming because we'd like validation on our data models we're putting into and getting out of the database, so we're going to use `pymodm` to help us interface with MongoDB in that manner. 

Here's the minimal example of a program that connects to a MongoDB database called `bme590` running on `localhost:27017`. 

```py
from pymodm import connect
from pymodm import MongoModel, fields

connect("mongodb://localhost:27017/bme590") # connect to database

class User(MongoModel):
    email = fields.EmailField(primary_key=True)
    first_name = fields.CharField()
    last_name = fields.CharField()
    password = fields.CharField()

u = User('user1@email.com', last_name='Ross', first_name='Bob')
u2 = User('user2@email.com', last_name='Ross', first_name='Rob')

u.save()
u2.save()

for user in User.objects.raw({"first_name":"Rob"}):
        print(user)
	print(user.first_name)
	print(user.last_name)
```
