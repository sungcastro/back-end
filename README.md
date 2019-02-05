<h1>Npm:</h1>

<p>npm i axios</p>

<h1>Notes</h1>

<h4>Getting Data</h4>
<p>The right place to call the server and get some data is in componentDidMount life cycle hook</p>
<p>The get method returns a promise.</p>
<p>A promise is an object that holds the result of an asynchronous operation</p>
<p>An asynchronous operation is an operation that is going to complete in the future, when we send an http request, there is always a delay
until we get the response.
</p>
<p>To get the response from a promise, we can use the method <b>await</b>.</p>
<p>Whenever await keyword is used in a function, we should decorated that function with <b>async</b> keyword.</p>

<h4>Creating Data</h4>
<p>The get method is used to get data and post to create data</p>
<p>axios.post(apiEndpoint, obj); Here because we'r creating data we need to include this data, in the body of the request, so we need to send this object to the server. So we pass this as the second argument of the post method.</p>

<h4>Updating Data</h4>
<p>There are two methods for updating data: patch and put</p>
<p>Patch is used to update two or more properties.</p>
<p>Put is used to update all properties.</p>

<p><b>axios.put(apiEndpoint + "/" + post.id, post);</b></p>
<p>As the first argument, we need to give the url (this references the entire post collection). But in this case we are updating a specific post, so we should include the post id in the url. As a second argument we need to pass the data to be sent to the server, so we need to send the entire post object</p>

<p><b>axios.patch(apiEndpoint + "/" + post.id, {title: post.title});</b></p>
<p>For patch method, we dont need to sent the entire post object, we can only send only one or more properties, and this are the properties we want to update</p>
