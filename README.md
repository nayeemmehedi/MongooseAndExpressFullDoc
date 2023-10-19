### indexing

            const mongoose = require('mongoose');
            
            const userSchema = new mongoose.Schema({
                username: {
                    type: String,
                    required: true,
                    unique: true, // This creates a unique index
                },
                email: {
                    type: String,
                    required: true,
                },
                age: {
                    type: Number,
                },
            });
            
// Define indexes

            userSchema.index({ email: 1 }); // Ascending index on the 'email' field
            userSchema.index({ age: -1 });  // Descending index on the 'age' field
            
            const User = mongoose.model('User', userSchema);
            
            module.exports = User;



Checking Indexes:

            db.collectionName.getIndexes()
            
drop index :
            
            const mongoose = require('mongoose');
            const User = require('./userModel'); // Import your Mongoose model
            
            mongoose.connect('mongodb://localhost/your_database', { useNewUrlParser: true, useUnifiedTopology: true });
            
            const indexName = 'your_index_name'; // Replace with the name of the index you want to drop
            
            User.collection.dropIndex(indexName, (error, result) => {
                if (error) {
                    console.error(`Error dropping index ${indexName}:`, error);
                } else {
                    console.log(`Index ${indexName} dropped successfully.`);
                }
                mongoose.connection.close(); // Close the MongoDB connection
            });
