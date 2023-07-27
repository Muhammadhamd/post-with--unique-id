
<h1>display post by unique id</h1>
<p>how to show a spefic post on another page by ID using js node.js</p>
        

    
   
   

```
** function postsbyid(postId){
        axios.get(`/posts/${postId}`)
        .then((response)=>{
            console.log(response.data);
        })
        .catch((e)=>{
            console.log(e);
        })
       } 
```

node js express code..... 


```
  Router.get(/posts/:postId, async (req,res,next)=>{
    const postId = req.params.postId;
    const post = await col.findOne({id : postId})
    
    if (post) {
    res.send()
    return;
}
else{
    res.send("no post found")
}
})
```

<h1>send data from frontend to backend</h1>
<p>backend</p>

```
Router.post("/post", async(req ,res , next)=>{
    // console.log('this is signup!', new Date());

    if (
         !req.body.text
    ) {
        res.status(403);
        res.send(`required parameters missing, 
        example request body:
        {
            title: "abc post title",
            text: "some post text"
        } `);
        return;
    }

    const inserData = await col.insertOne({
        id: nanoid(),
        text: req.body.text
    })
    console.log(inserData)
    // posts.unshift({
    //     id: nanoid(),
    //     text: req.body.text,
    // })

    res.send('post created');

})
```
<p>frontend</p>

```
 document.querySelector("#submitTodo").addEventListener("submit",(e)=>{
            e.preventDefault()
            let postText = document.querySelector("#text-todo").value;

            // baseUrl/api/v1/post
            axios.post(`/post`, {
                text: postText
            })
                .then(function (response) {
                    console.log(response.data);
                    // getAllPost();
                })
                .catch(function (error) {
                    // handle error
                    console.log(error);
                })
                getposts()
        })
```

<h1>Axios cnd link</h1>

```
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.js"></script>
```


