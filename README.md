### GeT Post Delete Update : 


   #### controller 

           const { homeSchemaValue } = require("../schema/home.schema");
        
### get req

            module.exports.Home = async (req, res) => {
              // const {ip, params, query, body, headers} = req
              const value = await homeSchemaValue.find({});
              res.send(value);
            };
        
 ### post req
 
        module.exports.HomePost = async (req, res) => {
          const mainValue = new homeSchemaValue(req.body);
          try {
            await mainValue.save();
        
            res.status(201).json(mainValue);
          } catch (error) {
            res.status(500).json({ error: error.message });
          }
        };


###POST ALL

        
     module.exports.postAllStore2 = async (req, res) => {
           try {
             // const value = ProductServiecPost(req, res);
             const value = await SchemaProduct.insertMany(req.body);
         
             res.json({
               status: "success",
               data: value,
             });
           } catch (err) {
             res.json({
               status: "error",
               message: err.message,
             });
           }
         };


### post / populate 

module.exports.postProduct2 = async (req, res) => {
  try {
    const getValue = new product2(req.body);

    const value = await getValue.save();

    const getProduct = await product2.find({ name: getValue.name });

    const updateValue = await store2.updateOne(
      { name: getProduct[0].category },
      { $push: { product: getProduct[0]._id } }
    );

    res.send({
      status: "success",
      value: updateValue,
    });
  } catch (error) {
    res.send({
      status: "failed",
      message: error.message,
    });
  }
};

         
 ### patch req
        
        module.exports.HomePatch = async (req, res) => {
          try {
            console.log(req.body);
        
            const user = await homeSchemaValue.findByIdAndUpdate(req.params.id, {
              $set: {
                email: req.body.email,
              },
            });
            if (!user) {
              return res.status(404).json({ message: "User not found" });
            }
            res.json("done");
          } catch (err) {
            res.status(500).json({ error: err.message });
          }
        };
        
        
 ### delete
 
        module.exports.HomeDelete = async (req, res) => {
          try {
            const user = await homeSchemaValue.findByIdAndDelete(req.params.id);
            if (!user) {
              return res.status(404).json({ message: "User not found" });
            }
            res.json({ message: "User deleted successfully" });
          } catch (err) {
            res.status(500).json({ error: err.message });
          }
        };


   ### patch specific id but price same those product product
  
      module.exports.HomeBulkupdateAll = async (req, res) => {
        try {
          const user = await homeSchemaValue.updateMany(
            { _id: req.body.ids },
            req.body.data,
            { runValidators: true }
          );
          if (!user) {
            return res.status(404).json({ message: "User not found" });
          }
          res.json("done");
        } catch (err) {
          res.status(500).json({ error: err.message });
        }
      
        //
        // this way give input
        //  {
        //     "ids" : [
        //         "64bd0ce83713d887d24d7b7b",
        //         "64bd0ce83713d887d24d7b7c"
        //     ],
        //     "data":{
        //         "city":"dhaka"
      
        //     }
        // }
      };

//product update many item and differnet price

      module.exports.HomeBulkupdateDiffernt = async (req, res) => {
        try {
          const products = [];

             req.body.ids.forEach((prod) => {
               products.push(homeSchemaValue.updateOne({ _id: prod.id }, prod.data));
             });
         
             const user = await Promise.all(products);
         
             if (!user) {
               return res.status(404).json({ message: "User not found" });
             }
             res.json("done");
     } catch (err) {
       res.status(500).json({ error: err.message });
     }

     // {
     //   "ids": [
     //       {
     //           "id": "64bd0ce83713d887d24d7b7b",
     //           "data": {
     //               "city": "dhaka"
     //           }
   
     //       },
     //           {
     //               "id": "64bd0ce83713d887d24d7b7c",
     //               "data": {
     //                   "city": "khulna"
     //               }
     //           }
     //       ]
     //   }
   };
   


### router 

    const express = require("express");
    const { Home, HomePost, HomePatch, HomeDelete } = require("../controller/home.controller");
    
    const routesHome = express.Router();
    
    routesHome.route("/")
    .get(Home)
    .post(HomePost)
    
    routesHome.patch("/:id",HomePatch);
    routesHome.delete("/:id",HomeDelete);
    
    
    
    
    
    module.exports = routesHome
