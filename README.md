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
