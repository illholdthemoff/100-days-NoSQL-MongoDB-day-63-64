The main difference between NoSQL databases to SQL databases, is that with NoSQL (NO) datavbased they do not have to have a predefined structure. Therefore there is a greater degree of freedom and thus less constraints when working with larger projects, and likely also scale betterererer too
Groupings of data in a NO database are called Collections which contain documents, which are basically like Javascript objects, but in appearance, since they are NOT Javascript

obcviously also since in NO databases they contain documents etc, they DO NOT have columnds or rows of information

![alt text](NODB-chart-1.jpg "Title");

Notice that here the two different documents in the colleciton on the left have different structures
this is the lack of needing to plan in motion

![alt text](NODB-chart-2.jpg "Title");

Also, relational data works differently in NO databases as well

![alt text](NODB-chart-3.jpg "Title");

Note the nested object circled in red. This is one of the features of NO databases
Also to note, the connection between the movies and the books, with the movies entry in the books document linking the ids together

When storing data in documents, it's best to do so based on the querys you will be running

![alt text](NODB-chart-4.jpg "Title");

You can grab documents from the database by typing db.yourDatabaseName.find()
If you want to grab paricular parts you can instead type db.yourDatabaseName.find({attribute: "value"}) to return any document or documents that match the attribute value you searched. Shown circled blue below

If you want to grab for example only the names of each document, you can type
db.yourDatabaseName.find({}, {name: 1}) and it will return the names in each document and by default also the id. The syntax here basically, the first set of braces is the conditional to control which documents are fetched (empty, therefore selects from all), and the second set of braces determines what to show (1 because if you remember, 1 is true.) Alternatively you can then have {name: 1, \_id: 0} if you don't want the ID to display for whatever reason, as \_id: 0 means setting its display to false. Shown circled in red below.
Also to note, when you grab a bunch of documnets, they are returned as an array of documents.

![alt text](NODB-output1.jpg "Title");

Soemthing to note, if you DO include a field in the second one, like with name up above, all other fields will be set to 0 and not displayed, since mongo will assume you just want that one (and also the ID by default)

When you only want to get ONE document, you can instead use db.yourDatabaseName.findOne({your conditions ehre}) to just return the first document that matches the entered parameters.

![alt text](NODB-output2.jpg "Title");

If you want to update your documents, you can use either updateOne or updateMany commands, but first it would be a good idea to find it by id first, .find({\_id: ObjectId("yourIdHere")})
This will return your document with the objectid wrapped around it. ObjectId is a built in value type, which is used in mongo for storing IDs

![alt text](NODB-output3.jpg "Title");

Onto updating a document. You would do
updateOne({\_id: ObjectId("yourIDHere")}, {$set: { attribute: "value" }} )
Or if you want to change a nested value,
updateOne({_id: ObjectId("yourIDHere")}, {$set: {"nestedField.attribute": "newValue"}})

Shown below. The results there will also return how many documents were found, and modified as well.

![alt text](NODB-output4.jpg "Title");

If you want to delete a document, the syntax at the start is similar to updating. it would be deleteOne or deleteMany, where you put in a matching parameter, and then mongo will find a matching document and delete it.

![alt text](NODB-output5.jpg "Title");

Like with updating, it will also tell you after how many documents were deleted.

Here is a good example of what a NoSQL database structure would look like

![alt text](NODB-chart-5.jpg "Title");

Note the nested document with the addresses on the restaurant document.
Addresses are nested because there is a chance multiple restaurants could share an address(like in a mall or something) and Types are a whole document for the purpose of not accidentally repeating tpyes (accidentally having both American and USA food etc). Reviews being sepearate makes sense because they are their own thing, and a single restaurant could have multuiple reviews as you can see from the restaurantID field in the reviews document.

ratingportal> db.reviews.insertOne({reviewer: "moff", rating: 3, text: "eh it was good I gues", date: new Date("2022-03-07"), restaurant: {id: ObjectId("6226c2ab0cc252b7168f2169"), name: "German BratHaus"} })

When for example trying to find a field in a document where the value is greater or less than or whatveer a given value, it would be db.yourDocument.find({attribute: {$gt: 4}})
In this case it will return all documents fields with an attribute greater than 4. Here are the general keys
lt = less than
lte = less than or equal
gt = greater than
gte = greater than or equal

If you wish to group a set of conditions, like greater than 1 but less than 3, it would be .find( $and: [{$gt: 1}, {$lt: 3}])
Again note that it is an array there

![alt text](NODB-output6.jpg "Title");
