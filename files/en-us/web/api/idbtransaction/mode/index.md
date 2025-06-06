---
title: "IDBTransaction: mode property"
short-title: mode
slug: Web/API/IDBTransaction/mode
page-type: web-api-instance-property
browser-compat: api.IDBTransaction.mode
---

{{ APIRef("IndexedDB") }} {{AvailableInWorkers}}

The **`mode`** read-only property of the
{{domxref("IDBTransaction")}} interface returns the current mode for accessing the
data in the object stores in the scope of the transaction (i.e., is the mode to be
read-only, or do you want to write to the object stores?) The default value is
`readonly`.

## Value

An object defining the mode for isolating access to
data in the current object stores:
A string defining the mode for isolating access to data in the current object stores.
The following values are available:

- `readonly`
  - : Allows data to be read but not changed.
- `readwrite`
  - : Allows reading and writing of data in existing data stores to be changed.
- `versionchange`
  - : Allows any operation, including ones that delete and
    create object stores and indexes.
    This mode is for updating the version number of transactions if the need is detected when calling {{domxref("IDBFactory.open()")}}.
    Transactions of this mode cannot run concurrently with other transactions.
    Transactions in this mode are known as _upgrade transactions_.

## Examples

In the following code snippet, we open a read/write transaction on our database and add
some data to an object store. Note also the functions attached to transaction event
handlers to report on the outcome of the transaction opening in the event of success or
failure. At the end, we log the mode of the current transaction using `mode`.
For a full working example, see our [To-do Notifications app](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([view example live](https://mdn.github.io/dom-examples/to-do-notifications/)).

```js
const note = document.getElementById("notifications");

// an instance of a db object for us to store the IDB data in
let db;

// Let us open our database
const DBOpenRequest = window.indexedDB.open("toDoList", 4);

DBOpenRequest.onsuccess = (event) => {
  note.appendChild(document.createElement("li")).textContent =
    "Database initialized.";

  // store the result of opening the database in the db variable.
  // This is used a lot below
  db = DBOpenRequest.result;

  // Run the addData() function to add the data to the database
  addData();
};

function addData() {
  // Create a new object ready for being inserted into the IDB
  const newItem = [
    {
      taskTitle: "Walk dog",
      hours: 19,
      minutes: 30,
      day: 24,
      month: "December",
      year: 2013,
      notified: "no",
    },
  ];

  // open a read/write db transaction, ready for adding the data
  const transaction = db.transaction(["toDoList"], "readwrite");

  // report on the success of opening the transaction
  transaction.oncomplete = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Transaction completed: database modification finished.";
  };

  transaction.onerror = (event) => {
    note.appendChild(document.createElement("li")).textContent =
      "Transaction not opened due to error. Duplicate items not allowed.";
  };

  // create an object store on the transaction
  const objectStore = transaction.objectStore("toDoList");

  // add our newItem object to the object store
  const objectStoreRequest = objectStore.add(newItem[0]);

  objectStoreRequest.onsuccess = (event) => {
    // report the success of the request (this does not mean the item
    // has been stored successfully in the DB - for that you need transaction.onsuccess)
    note.appendChild(document.createElement("li")).textContent =
      "Request successful.";
  };

  // Return the mode this transaction has been opened in (should be "readwrite" in this case)
  transaction.mode;
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using IndexedDB](/en-US/docs/Web/API/IndexedDB_API/Using_IndexedDB)
- Starting transactions: {{domxref("IDBDatabase")}}
- Using transactions: {{domxref("IDBTransaction")}}
- Setting a range of keys: {{domxref("IDBKeyRange")}}
- Retrieving and making changes to your data: {{domxref("IDBObjectStore")}}
- Using cursors: {{domxref("IDBCursor")}}
- Reference example: [To-do Notifications](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ([View the example live](https://mdn.github.io/dom-examples/to-do-notifications/)).
