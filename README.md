# mongodb-mover

A simple JavaScript function to move a MongoDB database from one server to another.

## Install

```bash
npm install mongodb-mover
```

## Usage

Use the `moveDatabase` function like this:

```javascript
const moveDatabase = require("mongodb-mover");

const sourceUrl = "mongodb://localhost:27017/sourceDb";
const destinationUrl = "mongodb://localhost:27017/destinationDb";
const databaseName = "myDatabaseToMove"; // The name of the database on the source to copy

// Optional: set how many documents to move at once (default is 10000)
const batchSize = 5000;

moveDatabase(sourceUrl, destinationUrl, databaseName, batchSize)
  .then(() => {
    console.log("Database moved successfully!");
  })
  .catch((error) => {
    console.error("Error moving database:", error);
  });
```

The function connects to your source and destination databases, copies all collections and their documents from the source database name you specify to the destination database, and then disconnects.

### Parameters

- `sourceUrl` (string): Connection string for the source MongoDB.
- `destinationUrl` (string): Connection string for the destination MongoDB.
- `databaseName` (string): The specific database on the *source* to copy.
- `batchSize` (optional, number): How many documents to copy in each step (default: 10000).

## License

[MIT](https://www.google.com/search?q=LICENSE)