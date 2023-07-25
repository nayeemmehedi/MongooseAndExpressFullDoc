schema.pre('save', () => console.log('Hello from pre save'));

schema.post('save', function(doc) {
  console.log('%s has been saved', doc._id);
});

userSchema.pre('save', function() {
  console.log(this.name); // { name: 'John' }
  console.log(this.age); // { age: 30 }
});
