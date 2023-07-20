### Doc start here : 

install :
    npm init -y
    npm install express cors nodemon 

starting code :

                  const express = require("express");
                  const cors = require("cors");
                  const mongoose = require("mongoose");
                 
                 


                  const app = express();
                  app.use(cors());
                  app.use(express.json());
                


                  mongoose.set("strictQuery", true);

                  mongoose
                    .connect(process.env.DATABASE_FILE || "mongodb://localhost:27017/mongoose1st")
                    .then(() => console.log("db conntected.."));



               app.get('/', (req, res) => {
                res.send('Hello World!')
              })

              
     app.listen(3000);
