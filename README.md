## How to need data 

## limit() -> 2 ta value dekhbe only

            db.collection.find({}).limit(2) 

## skip(3) -> mane first 3 ta skip krbe

           db.collection.find({}).skip(3).limit(3)

## sort -? boro thke choto ,choto thke boro

          db.collection.find({}).sort({age : -1}) -> boro thke choto akare 

## projection -> mane doc r vtr name,age , phone ase ami age chai na thle kmne hbe

             db.collection.find({}).projection({age : 0})  0 mane bad ,1 mane lgbe ..

## object r property

{subrance : { city :"dhaka"}} jodi amn object thke 

    db.collection.find({"subbrance.city":"dhaka"}).


## array of object :  activities: [ { city:"dhaka"}]

     db.collection.find({"activities.city":"dhaka"}).


# mongoose query :




## arrgiagtion most used 

$match: Filters documents based on specified criteria, similar to the find method.

$group: Groups documents by a specified key and performs various operations on the grouped data, such as calculating counts, sums, averages, etc.

$project: Shapes the documents in the pipeline, specifying which fields to include or exclude, and renaming fields.

$sort: Sorts the documents in the pipeline based on specified fields and order.

$limit: Limits the number of documents that pass through the pipeline.

$skip: Skips a specified number of documents in the pipeline.

$unwind: Deconstructs an array field from input documents, creating one document for each element in the array.

$lookup: Performs a left outer join with another collection, adding fields from the joined collection to the input documents.

$addFields: Adds new fields to documents, typically calculated or derived from existing fields.

$out: Writes the results of the aggregation to a new collection.

$facet: Allows you to perform multiple separate aggregations in a single stage, providing multiple sets of results.

$sample: Randomly selects a specified number of documents from the pipeline.

$redact: Implements data access control and restricts the fields returned based on certain rules.

$bucket: Categorizes documents into groups or buckets based on a specified expression and boundaries.

$bucketAuto: Automatically categorizes documents into buckets with evenly distributed boundaries.

$merge: Writes the results of the aggregation to a new or existing collection, similar to $out, but allows more flexibility.

 



             





