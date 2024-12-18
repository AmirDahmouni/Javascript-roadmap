## Callback Hell
**Callback hell** known as Pyramid of Doom occurs in JavaScript when multiple asynchronous operations are nested within one another using callbacks.
```javascript
fs.readFile("file1.txt", "utf8", (err, data1) => {
  if (err) throw err;
  console.log("File 1 content:", data1);

  fs.readFile("file2.txt", "utf8", (err, data2) => {
    if (err) throw err;
    console.log("File 2 content:", data2);

    fs.readFile("file3.txt", "utf8", (err, data3) => {
      if (err) throw err;
      console.log("File 3 content:", data3);

      console.log("All files have been read!");
    });
  });
});
```

## ✅ Solutions to Avoid Callback Hell
1. Use Promises
```javascript
const fs = require("fs").promises;

fs.readFile("file1.txt", "utf8")
  .then((data1) => {
    console.log("File 1 content:", data1);
    return fs.readFile("file2.txt", "utf8");
  })
  .then((data2) => {
    console.log("File 2 content:", data2);
    return fs.readFile("file3.txt", "utf8");
  })
  .then((data3) => {
    console.log("File 3 content:", data3);
    console.log("All files have been read!");
  })
  .catch((err) => {
    console.error("Error reading files:", err);
  });
```

2. Use async/await
```javascript
const fs = require("fs").promises;

async function readFiles() {
  try {
    const data1 = await fs.readFile("file1.txt", "utf8");
    console.log("File 1 content:", data1);

    const data2 = await fs.readFile("file2.txt", "utf8");
    console.log("File 2 content:", data2);

    const data3 = await fs.readFile("file3.txt", "utf8");
    console.log("File 3 content:", data3);

    console.log("All files have been read!");
  } catch (err) {
    console.error("Error reading files:", err);
  }
}
readFiles();
```

3. Modularize Callbacks
```javascript
const fs = require("fs");

function readFile1(callback) {
  fs.readFile("file1.txt", "utf8", callback);
}

function readFile2(callback) {
  fs.readFile("file2.txt", "utf8", callback);
}

function readFile3(callback) {
  fs.readFile("file3.txt", "utf8", callback);
}

readFile1((err, data1) => {
  if (err) throw err;
  console.log("File 1 content:", data1);

  readFile2((err, data2) => {
    if (err) throw err;
    console.log("File 2 content:", data2);

    readFile3((err, data3) => {
      if (err) throw err;
      console.log("File 3 content:", data3);
      console.log("All files have been read!");
    });
  });
});
```