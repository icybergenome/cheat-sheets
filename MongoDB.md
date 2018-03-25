# Mongo DB key points#
Basic fundamentals are:
* Instead of columns we have object type format with key and value pair known as **field**.
* Collection instead of table.
* Documents instead of records/rows:
  * Docs are structured in BSON similar to JSON(web language).
* NoSQL database(non relation).
  * Can't use joins to connect db tables, instead we use references to link docs.

## Advantages ##
* Easy Schema Iteration
* Scalable and better performance
* Object Oriented
* Agile Development that is it accommodates data which is structured, semi-structured and unstructured. Means you can add to your schema as need change.

## Document vs Collection ##
Document is a record in a MongoDB collection and basic unit of data in MongoDB collection. Documents looklike JSON but exist as BSON.

In BSON both the key and value have quotes:

>{
>"id" : "sjnsn1881"
}

Collection is a grouping of MongoDB documents. Typically all  docs in a collection have a similar or related purpose.

>{

>  "id": "123"

>  "article": "Hello World"

>}
>{

>  "id": "124"

>  "article": "New Doc"

>}

## Schema ##
Schema is a representation of a collections. It is somehow equivalent to collection. MongoDB is a schema less DB meaning we can insert any sort of data in the form of field in a same **collection** for different **Documents** . We have a solution for this in the form of ODM such as Mongoose.
## Common Commands ##
Command | Purpose |
--------|----------|
show [param] | list all the DBs/ Collections and etc
use *dbName* | make provided db active or create new in absense of it.
db.collectionName.**find()** | Show all documents in a collection, db prefix is always used when we have to access our active db.
.find({obj}) | return result on the basis of obj param. If empty then all documents would be returned
.pretty| make records pretty or more readable.
.createCollection | create new collection
.find({obj: {$gt or lt:num}}) | Filters greater than or less than
.find({obj: {$in:[arrayVals]}}) | Filter results on the basis of array values.
https://docs.mongodb.com/manual/reference/mongo-shell/

###Sample Queries###
>db.student.find({})
>
db.student.find({'name': 'Rachel'})
>
db.student.find({units: {$gt: 6}})
>
db.student.find({units: {$lt: 7}})
>
db.student.find({classes: {$in: ['history']}})
>
db.student.find({classes: {$in: ['history']}}).sort({units: -1})    // ascending
>
db.student.find({}).sort({name: 1})    // descending
>
db.student.find({}).sort({name: 1}).limit(2)
>
db.car.insert({
    name: 'honda',
    make: 'accord',
    year: '2010'
})
>
db.car.update({
    name: 'honda'
    },
    { $set: {
     name: 'ford'
    }
})
>
db.car.update({
    name: 'ford'
    },
    { $set: {
     transmission: 'automatic'
    }
}, {$upsert: true})

https://docs.mongodb.com/manual/tutorial/query-documents/

* JSON objects are used to write data to collections or to create a record/document. They are then converted into BSON format. ; at the end of a jSON object or "" quotes could also be used.

## Data types##
* String
* Number
* Date
* Array
* Boolean
* ObjectId (use as primary key for each document and for referencing a schema)
* Buffer (Video, Audio and images)
* Mixed (combines different types. one instance array other instance string)

###ObjectId###
Since Mongo generates the unique id for each document on it own. But we could modify the ObjectId.
>
const object = new ObjectId(); //Use constructor or a function
>
console.log(object);

https://docs.mongodb.com/manual/reference/method/ObjectId/

## Connection with Node/ExpressJS ##
* npm install mongodb
* https://expressjs.com/en/guide/database-integration.html#mongodb

Using **Mongoose** ODM(Object Data Mapper) to design the schema:
* npm install mongoose
* mongoose provides a method named **model()** which take arguments:
  * Name of model, this name would be used to create a collection in db.
  * collection's fields definitions i.e. type, required, minLength, default, trim and etc (Schema).
* Mongoose **schema()** constructor helps us to initialize schema definition.
