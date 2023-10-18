## handle module 


                        module.exports = nameBig
                        
                        const nameBig = require("./filename.js")


2nd way : 

            module.exports.name1 = name1
            module.exports.name2 = name2
            
            
             const {name1, name2}= require("./filename.js")

3rd way:

           module.exports ={nam1,name2}
           
            
            
             const {name1, name2}= require("./filename.js")


4th way : 


     module.exports.name1 =function name(){}

      const {name1}= require("./filename.js")

