# loopback-handbook

# table of contents

- [conventions](#conventions)
- [built-in models](#built-in-models)
- [commands](#commands)
  - [arc](#arc)
- more

# conventions

Sane conventions that you should use.

1. Model names are capitalized and singular, e.g. `Movie` and `CarPart`.
2. Properties are camelCase, e.g. `year` and `exhaustType`
3. Examples of date stamps should be in past tense, e.g.`created` and `lastUpdated`.
4. Foreign keys should be prefixed with the foreign entity's name, e.g. `userId` and `carId`.

These will map to your database schemas as well.

# built-in models

These models are available to your application, however you need to create the relevant tables.

1. `User`: Allows you to use [User API](http://docs.strongloop.com/display/public/LB/User+REST+API)
2. `AccessToken`: Allows you to use the [AccessToken API](http://docs.strongloop.com/display/public/LB/Access+token+REST+API)

You should try to use the built-in models instead of rolling in your own.

# commands

All commands require you to install strongloop as a global

```
npm i -g strongloop
```

## arc

Launches the StrongLoop GUI, let's you define loopback models and more. Also includes profiling tools.

```
slc arc
```

## loopback:app

Creates an app.

```
slc loopback:app [<name>]
```
