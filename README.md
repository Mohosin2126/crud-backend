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


## Post 
### Endpoint:"/withlist"
### Method:"post"


```js
app.post("/wishlist", async (req, res) => {
  const cart = req.body;
  const result = await wishlistCollection.insertOne(cart);
  res.send(result);
});

```


## Delete
### Endpoint:"/withlist/:id"
### Method:"delete"


```js
app.delete("/wishlist/:id",async(req,res)=>{
  const id=req.params.id
  const query={_id: new ObjectId(id)}
  const result=await wishlistCollection.deleteOne(query)
  res.send(result)
})

```



