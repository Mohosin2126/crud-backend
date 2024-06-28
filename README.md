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
### Endpoint:"/users/:email"
### Method:"Get"


```js
app.get("/users/:email", async (req, res) => {
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

## Post (For Double)
### Endpoint:"/users"
### Method:"post"

```js
app.post("/users",async(req,res)=>{
  const user=req.body 
const query={email:user.email}
const existingUser=await userCollection.findOne(query)
if (existingUser){
  return res.send({message:"user already exist",insertedId:null})
}
 
  const result=await userCollection.insertOne(user)
  res.send(result)
})
```


## Update
### Endpoint:"/users/admin/:id"
### Method:"patch"

```js
 app.patch('/users/admin/:id',async(req,res)=>{
  const id=req.params.id 
  const filter ={_id: new ObjectId(id)}
//   update field
  const updatedDoc={
    $set:{
      role:"admin"
    }
  }
  const result =await userCollection.updateOne(filter,updatedDoc)
  res.send(result)
 })

```


## Delete 1
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

## Delete 2
### Endpoint:"/withlist/:id"
### Method:"delete"



```js
app.delete("/withlist/:id", async (req, res) => {
      const id=req.params.id
      const query = {
        id: new ObjectId(id),
      };
      try {
        const result = await wishlistCollection.deleteOne(query);
        res.send(result);
      } catch (error) {
        console.error("Error deleting application:", error);
        res.status(500).json({ error: "Internal Server Error" });
      }
    });
    ```


