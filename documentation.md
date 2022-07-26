============================================
============================================
## EXAMPLE DOCUMENTATION
### Ask for the Home Page
#### Step 1
Predicted Request components:
- Method: GET
- URL: http://localhost:5000/
- Headers:
      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
      Accept-Encoding: gzip, deflate, br
      Accept-Language: en-US,en;q=0.9
      Connection: keep-alive
      Host: localhost:5000
      Sec-Fetch-Dest: document
      Sec-Fetch-Mode: navigate
      Sec-Fetch-Site: none
      Sec-Fetch-User: ?1
      Upgrade-Insecure-Requests: 1
      User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36
      sec-ch-ua: ".Not/A)Brand";v="99", "Google Chrome";v="103", "Chromium";v="103"
      sec-ch-ua-mobile: ?0
      sec-ch-ua-platform: "Windows"
- Body: none

Predicted Response components:
- Status Code: 200
- Headers:
      X-Powered-By: Express
      Content-Type: text/html; charset=utf-8
      Content-Length: 826
      Date: Tue, 26 Jul 2022 22:38:43 GMT
      Connection: keep-alive
      Keep-Alive: timeout=5
- Body: HTML page with navigation links to other pages

#### Step 2
In your browser open the chrome dev tools, navigate to [http://localhost:5000] and make a GET request for the Home Page (type "/" into the URL after 5000 and hit "enter").
Explore the "network" tab and find where you can compare your predicted request/response components to the actual components.

#### Step 3
If your prediction was wrong, try to understand why it was incorrect and then update your documentation to the correct request/response components.

Congratulations! You have performed a GET request to / showing the home page of our e-commerce
website. Move on to the next request/response documentation.

* Note
    - Headers contain many keys, but for this exercise focus on **Content-Type** and **Location**.

=============================================
=============================================

### Ask for a page that doesn't exist

Request components:
- Method: GET
- URL: http://localhost:5000/dogs
- Headers: same as above
- Body: same as above

Response components:
- Status code: 404
- Headers: same as above
- Body: HTML page saying 404 page not found

### Ask for the products list page

Request components:
- Method: GET
- URL: /products
- Headers: same as above
- Body: same as above

Response components:
- Status code: 200
- Headers: same as above
- Body: HTML page with the only product

### Ask for the product detail page

Here's an example product on the server:

| detail      | value                                                      |
| ----------- | ---------------------------------------------------------- |
| productId   | 1                                                          |
| name        | "Facial Cleansing Brush"                                   |
| description | "Reaches deep pores to cleanse oil, dirt, and blackheads." |
| price       | 23.99                                                      |
| categories  | "beauty", "electronics"                                    |

Request components:
- Method: GET
- URL: /products/1
- Headers:
- Body:

Response components:
- Status code: 200
- Headers:
- Body: html page for the product

### Ask for the create new product page

Request components:
- Method: GET
- URL: /products/new
- Headers:
- Body:

Response components:
- Status code: 200
- Headers:
- Body: html page to create a product

### Submit a new product

Remember, for a traditional HTML web server, whenever a successful `POST`
request is sent to the server, the server should respond with a redirection to
a page.

After successful submission, user should be looking at the product detail page.

Here are the categories on the server:

| tag         | name           |
| ----------- | -------------- |
| grocery     | Grocery        |
| electronics | Electronics    |
| beauty      | Beauty         |
| toys-games  | Toys and Games |
| health      | Health         |
| furniture   | Furniture      |
| clothing    | Clothing       |

* Note: In Chome dev tools, if the "body" of a request exists, it will appear
in the network tab as "payload".

Request components:
- Method: POST
- URL: /products
- Headers:
      Content-Type: application/x-www-form-urlencoded
      Referer: http://localhost:5000/products/new
- Body:
      name=New+Item+1&description=This+is+the+first+new+item&price=10.99&categories=electronics

Response components:
- Status code: 302
- Headers:
      Location: /products/2
- Body: html page of the product

### Ask for the edit product page

Request components:
- Method: GET
- URL: /products/2/edit
- Headers:
- Body:

Response components:
- Status code: 200
- Headers:
- Body: html page to edit product

### Submit an edit for an existing product

After successful submission, user should be looking at the product detail page.

Request components:
- Method: POST -> GET
- URL: /products/2 -> /products/2
- Headers:
      Content-Type: application/x-www-form-urlencoded
      Referer: http://localhost:5000/products/new
- Body:
      name=New+Item+1&description=This+is+the+first+new+item&price=12.99&categories=electronics

Response components:
- Status code: 302 -> 200
- Headers:
      Location: /products/2
- Body: html page of the product

### Submit a delete for an existing product

After successful submission, user should be looking at the products list page.

Request components:
- Method: POST -> GET
- URL: /products/2/delete -> /products
- Headers:
- Body:

Response components:
- Status code: 302 -> 200
- Headers:
      Location: /products
- Body: html page for all products

### Submit a new review for a product

After successful submission, user should be looking at the product detail page.

Here's an example review on the server:

| detail     | value                  |
| ---------- | ---------------------- |
| reviewId   | 1                      |
| comment    | "I love this product!" |
| starRating | 5                      |
| productId  | 1                      |

Request components:
- Method: POST -> GET
- URL: /products/1/reviews
- Headers:
      Content-Type: application/x-www-form-urlencoded
      Referer: http://localhost:5000/products/1
- Body:
  comment=I+hate+this+product%21&starRating=1

Response components:
- Status code: 302 -> 200
- Headers:
      location: products/1
- Body: product page

### Ask for the edit review page for a product

Request components:
- Method: GET
- URL: /reviews/1/edit
- Headers:
      Referer: http://localhost:5000/products/1
- Body:

Response components:
- Status code: 200
- Headers:
- Body: html page for the review edit

### Submit an edit for an existing review

After successful submission, user should be looking at the product detail page.

Request components:
- Method: POST -> GET
- URL: /reviews/1
- Headers:
      Content-Type: application/x-www-form-urlencoded
      Referer: http://localhost:5000/reviews/1/edit
- Body:
    comment=I+love+this+product%21&starRating=4

Response components:
- Status code: 302 -> 200
- Headers:
    location: products/1
- Body:

### Submit a delete for an existing review

After successful submission, user should be looking at the product detail page.

Request components:
- Method: POST -> GET
- URL: /reviews/2/delete -> /products/1
- Headers:
     Content-Type: application/x-www-form-urlencoded
     Referer: http://localhost:5000/products/1
- Body:

Response components:
- Status code: 302 -> 200
- Headers:
      Location: /products/1
- Body: html page for current product

### Ask for all the products in a particular category by tag of the category

Request components:
- Method: GET
- URL: /categories/beauty/products
- Headers:
- Body:

Response components:
- Status code: 302
- Headers:
- Body: page with items in the beauty category

### Ask for the best-selling product

Look for clues in the HTML pages from the prior responses for what the route should be.

Request components:
- Method: GET
- URL: /products/best-selling
- Headers:
- Body:

Response components:
- Status code: 200
- Headers:
- Body:
