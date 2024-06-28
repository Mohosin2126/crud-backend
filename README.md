## Get All Users
### Endpoint:"/users"
### Method:"Get"


```js
app.get("/users", async (req, res) => {
  const result = await userCollection.find().toArray();
  res.send(result);
});


```
### output:

```js
[
  {
    "_id": "user1_id",
    "name": "John Doe",
    "email": "john.doe@example.com"
  },
  {
    "_id": "user2_id",
    "name": "Jane Doe",
    "email": "jane.doe@example.com"
  }
]

```


## Get User by Email
### Endpoint:"/users"
### Method:"Get"


```js
app.get("/users", async (req, res) => {
  const email = req.query.email;
  const query = { email: email };
  const result = await userCollection.find(query).toArray();
  res.send(result);
});


```
### output:

```js
[
  {
    "_id": "user1_id",
    "name": "John Doe",
    "email": "john.doe@example.com"
  }
]


```



