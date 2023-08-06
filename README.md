const hash = bcrypt.hashSync(myPlaintextPassword, saltRounds);

bcrypt.compare(someOtherPlaintextPassword, hash).then(function(result) {
    // result == false
});
