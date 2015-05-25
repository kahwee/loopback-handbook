# autoupdate your existing db

The following code auto upgrades your db:

```js
var async = require('async');

module.exports = function(app) {
  var mysqlDs = app.dataSources.db;
  async.parallel({
    people: async.apply(createMovies),
    users: async.apply(createUsers),
  }, function(err, results) {
    if (err) throw err;
  });

  // create reviewers
  function createMovies(cb) {
    mysqlDs.autoupdate('Movie', function(err) {
      if (err) return cb(err);
      app.models.Movie.find({where: {name:'Bob', year: 2015}}, function(err, movies) {
        if (movies.length === 0) {
          app.models.Movie.create([{
            name: 'Bob',
            year: 2015
          }], cb);
        }
      });
    });
  }

  function createUsers(cb) {
    mysqlDs.autoupdate(['User', 'AccessToken', 'ACL'], function(err) {
      if (err) return cb(err);
      app.models.User.find({where: {username:'kahwee'}}, function(err, users) {
        if (users.length === 0) {
          app.models.User.create([{
            username: 'kahwee',
            email: 'tengkahwee@gmail.com',
            password: '!password1'
          }], cb);
        } 
      });
    });
  }
};

```
