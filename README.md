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

 



             





