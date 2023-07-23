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
      email: String
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
#### 10.  enum:
     {
      values: ['Coffee', 'Tea'],
      message: '{VALUE} is not supported'
    }


#### 11 minLength,  maxlength 

   maxlength: 20 //min string and max string

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



    





