  ## jodi amra kichu bad deye baki sob dekhaite chai
  
      const value = await homeSchemaValue.find({},"-first_name")

## jodi amra exctly kichu jnis dkhyte chai

       const value = await homeSchemaValue.find({},"first_name")

## limit - jodi use kri 1 dele 1 ta asbe

     const value = await homeSchemaValue.find({}).limit(1)

## sort - jodi use kri 

   desc - niche thke upor
   asc - upor thke niche, choto thke boro

     const value = await homeSchemaValue.find({}).sort({quentity:-1})

## select - jodi use kri 1 dele 1 ta asbe

     const value = await homeSchemaValue.find({}).limit(1)


## where 

  const value = await homeSchemaValue.where("name").equals("chals").where("quntity").gt(20)






