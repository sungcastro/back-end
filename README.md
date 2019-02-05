<h1>Npm:</h1>

<p>npm i axios</p>

<h1>Notes</h1>

<h5>Getting Data</h5>
<p>The right place to call the server and get some data is in componentDidMount life cycle hook</p>
<p>The get method returns a promise.</p>
<p>A promise is an object that holds the result of an asynchronous operation</p>
<p>An asynchronous operation is an operation that is going to complete in the future, when we send an http request, there is always a delay
until we get the response.
</p>
<p>To get the response from a promise, we can use the method <b>await</b>.</p>
<p>Whenever await keyword is used in a function, we should decorated that function with <b>async</b> keyword.</p>

<h5>Creating Data</h5>
<p>The get method is used to get data and post to create data</p>
<p>axios.post(apiEndpoint, obj); Here because we'r creating data we need to include this data, in the body of the request, so we need to send this object to the server. So we pass this as the second argument of the post method.</p>
