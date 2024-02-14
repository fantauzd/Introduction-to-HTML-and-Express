1. Homepage
Update index.html so that this page has an h1 element and includes links using the anchor element to the following 2 HTML pages that you will create
Stock Order Page
Stock Search Page
In addition to the h1 element and the 2 anchor elements, you can optionally add welcome text on this page to describe the web app.
2. Stock Order Page
Create an HTML file that displays the following information
An HTML table with the data provided in the file stocks.js, and
An HTML form to order stocks
This page must also have an h1 element in addition to the HTML table and the HTML form.
HTML Table:
The table must have one row of data for each stock in the file stocks.js
Each row in the HTML table must have the following 3 columns
Company name
Stock symbol
Current price
The table must have a header row.
The table must correctly use the thead and tbody tags.
Form to order stocks:
Underneath the HTML table, you must provide controls for the user to submit a stock order. The following controls must be provided:
A select element with a drop-down containing all the stock symbols from stocks.js
An input element of type number for entering the quantity to buy
A button to submit the form.
When the form is submitted, an HTTP request must be sent to the server running at localhost:3000
The request must include the user's selection for the stock symbol and the quantity they want to buy.
The server will send back the Stock Order Response which is displayed in the browser.
You are free to choose the URL for the form action, or to be more precise, you are free to choose the "path to resource" part of the URL.
See Exploration — URL for the parts of a URL should you need to review the topic.
You can choose either GET or POST as the method for the form.
Note: This page must be a static HTML file. No JavaScript code should be executed to generate or modify the page when a request comes for this page.
In the page type the HTML code for the HTML table using the data from the file stocks.js.
Similarly type in the HTML code for the select drop-down using the data from the file stocks.js.
Don't dynamically generate this page via a route handler in stocks.js for each request.
Stock Order Response
Add a route handler in server.js which gets executed when the server receives the request sent by the browser when the form on Stock Order Page is submitted.
This route handler must dynamically generate and send back the appropriate HTTP response.
Your JavaScript code must use the variable stocks  to access the stock data and you must not hard-code the data from the file stocks.js in your JavaScript code.
You must write a function findStockBySymbol(...).
This function must take one argument, a string value with the symbol of the stock to look up.
The argument to the function must the symbol of the stock (not the name of the stock).
You cannot pass the request object and/or the response object to this function.
This function must return the stock object from the variable stocks that matches the symbol passed as the argument to the function.
This function must return the matching stock object, i.e., it must not return a property or some properties of the stock object, but must return the object.
This function doesn't need to handle the case where it is called with a symbol that doesn't exist in the variable stocks
Your route handler must call this function findStockBySymbol(...) passing it the stock symbol sent in the HTTP request and then use the object returned by the function to generate the response.
The response must be a string value (not a JSON) with the following format:
You placed an order to buy N stocks of CompanyName. The price of one stock is $Y and the total price for this order is $Z
For example:
You placed an order to buy 10 stocks of Splunk. The price of one stock is $137.55 and the total price for this order is $1375.5
Optional
You can use string interpolation to create this string.
You can use toLocaleString() to format the price values using the currency formatLinks to an external site. specific to the US.
Sending the response
To send the response, your route handler must call res.send() with one argument which is the string with the required format described above.
You don't need to call any other methods on the response object. 
Note that when you call res.send()
If the argument to res.send() is a string value, by default Express automatically sets the Content-Type header in the response to text/html. So you don't need to explicitly set this header.
Again, by default Express sets the response status code to 200. So you don't need to explicitly set the status code of the response.
3. Stock Search Page
Create an HTML file with a form that provides two choices to the user for searching the stock data
Highest price
Lowest price
You must use radio buttons to provide these 2 choices to the user, and provide a button to submit the form.
This page must also have an h1 element in addition to the HTML form.
You are free to choose the URL for the action of the form, or to be more precise, you are free to choose the "path to resource" part of the URL.
You can choose either GET or POST as the method for the form.
When the form is submitted, an HTTP request must be sent to the server running at localhost:3000
The request must include the user's choice of the search criterion.
The server will send back the Stock Search Response which is displayed in the browser.
Note: This page must be a static HTML file. No JavaScript code should be executed to generate or modify the page when a request comes for this page.
Stock Search Response
Add a route handler in server.js which gets executed when the server receives the request sent by the browser when the form on Stock Search Page is submitted
This route handler must dynamically generate and send back the appropriate HTTP response.
Your JavaScript code must use the variable stocks  to access the stock data and you must not hard-code the data from the file stocks.js in your JavaScript code.
You must write a function findStockByPrice(...).
This function must take one argument which tells the function whether to find the stock with the lowest price or the one with the highest price.
You cannot pass the request object and/or the response object to this function.
It must return the object from the variable stocks that matches the criterion passed as the argument.
This function must return the stock object matching the specified criterion, i.e., it must not return a property or some properties of the stock object, but must return the object.
In case of a tie, the function can return any one of the objects that meet the specified criterion.
This function must find the relevant stock "on the fly," i.e., you must not hard-code or permanently store the information about which stock has the highest price and which stock has the lowest price.
Your route handler must call this function findStockByPrice(...) passing it the criterion sent in the HTTP request and then use the object returned by the function to generate the response.
Your route handler can call the function with the exact value sent in the HTTP request. But this is not required.
This means that you can choose to map the value received in the request to some other value describing the user choice and call the function with that value.
Sending the response
To send the response, your route handler must call res.send() with one argument which is the object returned by the function findStockByPrice(...) , i.e., don't send a string in the response.
You don't need to call any other methods on the response object. 
Note that when you call res.send()
If the argument to res.send() is an object, by default Express automatically sets the Content-Type header in the response to application/json. So you don't need to explicitly set this header.
Again, by default Express sets the response status code to 200. So you don't need to explicitly set the status code of the response.
What to Turn In?
To Zip/compress an archive of files and folders, select the ones you want, right-click, then choose compress, zip, or archive. The resulting file .zip archive will appear in the same folder. Use Node version 20.x for this assignment:
Don't use Node.js version 15.x or 16.x or 17.x or  18.x or 19.x or 21.x.
Submit a single zip file with your code.  
This zip file must be named youronid_assignment3.zip where youronid should be replaced by your own ONID.
E.g., if chaudhrn was submitting the assignment, the file must be named chaudhrn_assignment3.zip.
When you resubmit a file in Canvas, Canvas can attach a suffix to the file, e.g., the file name may become chaudhrn_assignment3-1.zip. Don't worry about this name change as no points will be deducted because of this.
In the zip file, you must include all the code for your application, but do not include the node_modules directory.
The grader will unzip your file, go to the root directory, run npm install and then run npm start to start your application and test it.
