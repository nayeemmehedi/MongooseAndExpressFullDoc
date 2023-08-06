### Doc start here : 

install :

            npm init -y
            npm install express cors nodemon mongoose

starting code :

        const express = require("express");
        const cors = require("cors");
        const mongoose = require("mongoose");
        const app = express();
        
        app.use(express.urlencoded({ extended: true }));
        app.use(express.json());
        app.use(cors());
        
        
        mongoose.set("strictQuery", true);
        
        mongoose
          .connect(
            process.env.DATABASE_FILE || "mongodb://0.0.0.0:27017/express1stLearn"
          )
          .then(() => console.log("db conntected..")
          );
        
          app.get('/', (req, res) => {
            res.send('Hello World!')
          })
        
        app.listen(4000);
