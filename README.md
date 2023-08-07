### schema doc 

### basic example

    const mongoose = require('mongoose');
    
    const { Schema } = mongoose;
    
    const homeSchema = new Schema({
      fist_name: String, 
      comments: [{ body: String, date: Date }],
      date: { type: Date, default: Date.now },
      hidden: Boolean,
      meta: {
        votes: Number,
        favs: Number
      },
      fist_name: {
    type: String,
    required: true,
    minLength: 5,
    maxLength: 15,
  },
  
      email: {
        type: String,
        required: true,
        match:[ /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|.(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/,"Email not matched."]
         
      },
      gender: {
        type: String,
        enum: {
          values: ["male", "female"],
          message: "{VALUE} must be male/female",
        },
      },
      color: {
        type: String,
        required: true,
      },
      city: {
        type: String,
        required: true,
      },
      job_title: {
        type: String,
        required: true,
      },
    
      airport: {
        type: String,
        required: true,
      },
    });
    
    const home =  mongoose.model('Blog', homeSchema);
    
     module.exports.homeSchemaValue = home




type of schema : 

    String
    Number
    Date
    Buffer
    Boolean
    Mixed
    ObjectId
    Array
    Decimal128
    Map
    UUID
    BigInt


# SchemaType Options

1. type

      name: { type: String },
      nested: {
        firstName: { type: String },
        lastName: { type: String }
      }

2 required 

**.All SchemaTypes have the built-in required validator. The required validator uses the SchemaType's checkRequired() function to determine if the value satisfies the required validator.

     required: function() {
          return this.bacon > 3;
        }


**.Numbers have min and max validators.

   
     min: [6, 'Too few eggs'],


**.Strings have enum, match, minLength, and maxLength validators.

     required: [true, 'Why no bacon?']
      enum: ['Coffee', 'Tea'],
      
3.default
4.validate

     validate: {
          validator: function(v) {
            return /\d{3}-\d{3}-\d{4}/.test(v);
          },
          message: props => `${props.value} is not a valid phone number!`
        },

#### 5.unique :boolean
#### 6.lowercase
#### 7.uppercase
####  8.trim

#### 9.match: /^[a-zA-Z0-9_-]{3,20}$/

match:[/^[a-zA-Z0-9_-]{3,20}$/,"Email not matched."]
example 

        email: {
            type: String,
            required: true,
            unique: true,
            match: /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/, // Regular expression to match a valid email address
            validate: {
              validator: function (value) {
                return /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/.test(value);
              },
              message: 'Please provide a valid email address',
            },
          },
#### 10.  enum:
1way:
     enum: {
        values: ["male", "female"],
        message: "{VALUE} must be male/female",
      },

2way:
 product :{
 type :String,
 enum :['Coffee', 'Tea']
}


#### 11 minLength,  maxlength 

   maxlength: 20 //min string and max string
    maxlength:[20,"must 20 carector"]
   

date :

         dateField: {
            type: Date,
            validate: [
              {
                validator: function (value) {
                  // 'this' refers to the current document being validated
                  return value >= this.min; // Check if value is greater than or equal to the 'min' property of the document
                },
                message: 'Date is less than the minimum allowed value.',
              },
              {
                validator: function (value) {
                  return value <= this.max; // Check if value is less than or equal to the 'max' property of the document
                },
                message: 'Date exceeds the maximum allowed value.',
              },
            ],
          },

12.ref 

     author: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'User',
      },

      supplier:{
       type:mongoose.Schema.Types.ObjectId,
        ref:"Supplier"
     }


13.Date

    date: { type: Date, default: Date.now }

14.unique: true/ false
15.timestamps: true



# Importent example 


        const mongoose = require("mongoose");
        const { Schema } = mongoose;
        var validator = require("validator");
        
        const signUpSchema = new Schema({
          name: {
            type: String,
            minLength: 4,
            maxLength: 20,
            required: true,
          },
        
          email: {
            type: String,
            validate: [validator.isEmail, "Please enter a valid email"],
            required: true,
          },
        
          password: {
            type: String,
            // validate: {
            //   validator: (value) =>
            //     validator.isStrongPassword(value, {
            //       minLength: 6,
            //       minLowercase: 1,
            //       minNumber: 1,
            //       minUppercase: 1,
            //       minSymbols: 1,
            //     }),
            //   message: "Password {VALUE} is not Strong.",
            // },
            required: true,
          },
          confirmPassword: {
            type: String,
            // required: true,
            validate: {
              validator: function (value) {
                return value === this.password;
              },
              message: "Password dont match",
            },
          },
          imgUrl: {
            type: String,
            validate: [validator.isURL, "Please provide img url"],
          },
          status :{
            type : String,
            default : "buyer",
            enum:["buyer","sell-team","admin"]
          }
        });
        
        module.exports.signUP = mongoose.model('signUp', signUpSchema);
        
        
        

    





