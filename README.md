<h1>Npm:</h1>

<p>npm i axios</p>

<h1>Notes</h1>

<h3>Getting Data</h3>
<p>The right place to call the server and get some data is in componentDidMount life cycle hook.</p>
<p>The get method returns a promise.</p>
<p>A promise is an object that holds the result of an asynchronous operation.</p>
<p>An asynchronous operation, is an operation that is going to be completed in the future, when we send an http request, there is always a delay
until we get the response.
</p>
<p>To get the response from a promise, we can use the method <b>await</b>.</p>
<p>Whenever await keyword is used in a function, we should decorated that function with <b>async</b> keyword.</p>

<h3>Creating Data</h3>
<p>The <b>get</b> method is used to get data and <b>post</b> to create data.</p>
<p>axios.post(apiEndpoint, obj);  
<br>
Here, because we'r creating data we need to include it in the body of the request, so we need to send this object to the server. So obj is passed as the second argument of the post method.</p>

<h3>Updating Data</h3>
<p>There are two methods for updating data: <b>patch</b> and <b>put</b>.</p>
<p><b>Patch</b> is used to update two or more properties.</p>
<p><b>Put</b> is used to update all properties.</p>

<p><b>axios.put(apiEndpoint + "/" + post.id, post);</b></p>
<p>As the first argument, we need to give the url (this references the entire post collection). But in this case we are updating a specific post, so we should include the post id in the url. As a second argument we need to pass the data to be sent to the server, so we need to send the entire post object</p>

<p><b>axios.patch(apiEndpoint + "/" + post.id, {title: post.title});</b></p>
<p>For patch method, we dont need to sent the entire post object, we can only send only one or more properties, and this are the properties we want to update</p>

<h3>Optimistic vs Pessimistic</h3>
<p>Optimistic updates, first you keep a reference to the original state and then update the Ui before calling the server, then, wrap the call to the server in a try and catch block.</p>
<p>In order to detect errors, we need to wrap the call to the server with a <b>try, catch block</b>.</p>
<p><b>Try,</b> makes the call to the server.</p>
<p>
<b>Catch,</b> 
recives (ex) which means exeption or an 'error', and  this is the moment where we display an error to the user and revert the screen, by updating the state to the previous state.
</p>

<h3>Expected vs Unexpected errors</h3>

<h4>Expected</h4>

<p>Expected errors are apiEndpoints predict and return.</p>
<p>If we try to delete a post in an invalid id, the server will return a response with a status code <b>404</b> which means not found.</p>
<p>If we try to submit a form with invalid data <b>400</b> which means bad request.</p>
<p>In the http protocol, this errors are defined as CLIENT ERRORS. </p>

<h4>Unexpected</h4>
<p>Unexpected errors are errors that techically should not happen under normal circumstances.</p>
<p>If the network is down, server down, db down, bug.</p>
<br>
<p>The (ex) 'Exception' object has two properties, <b>Request</b> and <b>Response</b> </p>
<p> <b>ex.response</b> is set if we get a succesful response from the server, if the network is down, or the server crash, we wont get a response so this property will be null.</p>

<p> <b>ex.request</b> is set if we can sucessfully submit a request to the server, otherwise its going to be null.</p>

<h3>Handling Unexpected Errors Globally</h3>

<h4>Interceptors in axios</h4>

<p>We can intercept our requests before going out and our responses that we get.</p>
<p><b>axios.interceptors.response.use()</b></p>
<p>use() method takes to parameters, both parameters are functions that will be called. The first function that will be called <b>axios.interceptors.response.use(success)</b> if the response is succesful.</p>

<p>
And the second function will be called if the response <b>axios.interceptors.response.use(success, error)</b>
includes an error. This function will be executed everytime we have a response with an error. 
<br>
To pass control to our catch block, we need to return a reject promise. <b> return Promise.reject() </b> this will create a rejected promise, and we simply include this error in our promise object <b> return Promise.reject(error) </b>.
</p>

<h3>Extracting a Reusable Http Service</h3>

<h4>httpService.js</h4>
<p>The defult object should have 4 methods. Get, post, put, and delete. 
Just like the axios object.</p>
