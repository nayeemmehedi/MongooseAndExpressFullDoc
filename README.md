### schema doc 


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

5.unique :boolean
6.lowercase
7.uppercase
8.trim
9.match

    





