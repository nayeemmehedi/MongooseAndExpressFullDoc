### Mongodb operator

     const value = await homeSchemaValue.find({gender: {$in:["male","female"] }});
      res.send(value);
   ...............
   
    $eq 
    $ne
    
    $gt
    $gte
    
    $in - [inside array ]
    $nin
    
    $lt
    $lte
    ........
### logic
    
    $and
    $or
    $nor
    $not




