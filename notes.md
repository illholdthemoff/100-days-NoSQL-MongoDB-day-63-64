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
