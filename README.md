# Project Ideas 

## WHEN should we read this

We can approach the following project ideas once we got a solid understanding of:

- UI basics (HTML / CSS)
- DOM manipulation
- NodeJS basics
- Asynchronous JavaScript (Promises, Async / Await, Callbacks, Fetch)

## Types of applications

- Blog / Newspage
- Social Media page
- Commercial / Shop
- Browser games
- Live-Data services (e.g. stocks, sports ticker, chat)

### Device specific applications

- Web App
- Mobile App
- Desktop App

## Project suggestions - initial list

    Backend
    - Terminal chat
    - Terminal rock-paper-scissors
    
    Browser
    - Rock paper scissors
    - Minesweeper
    - Flappy Bird
    - Tetris

    Fullstack
    - Shopping cart
    - Mini-Shop with Checkout, Payment Processing and Order Email
    - Social login (Login via Facebook, Google, GitHub, etc)

    Real-Time / Streaming
    - Stock Trader
    - Web Chat
    - Video course app

    Other:
    - Deployment with Docker
    - Desktop App for private data
    - Mobile Pizza Order App

---

## Entry level (1-3 days)

### Rock paper scissors with a browser UI

- In UI you pick a name and select a move
- The opponents move will be a random move
- Write the function to check who won
- Display the winner and offer a new game
- Bonus: Store the game result in the browser
=> research how to use local storage

### Terminal games (backend only)
   
Research (foundation for all games): 

- terminology "Socket" and "TCP"
- the net package of node.js
- how to open a port / create a socket
- how to listen to incoming calls
- how to listen to keyboard events
- how to write messages to a socket

#### Rock paper scissors

- Setup a TCP game server
- On an incoming request: 
    - Let the user choose a user name that will be shown a prefix to his messages, like to: [rob]: Hello
    - you pick a move via stdin, player picks random move

#### Terminal chat

- Simulate a chat between two parties via a socket
- Create a script tcp-server.js
- Create a script tcp-client.js
- On an incoming request: Write a chat welcome message
- On typing and sending a new chat message: Write the message to the socket so the other party receives it
    - Both server and client can send and receive messages from the other party
- When client closes connection (via CTRL+C)
    - Server should listen for the connection closing event
    - Server should write the chat log to a file chat_history.txt

---

## Medium (up to 2 weeks)

### Browser games

#### Flappy bird

Demo: https://flappybird.io/

- Create a browser game with animations
- Choose graphics from pixabay, unsplash or other free image resources
- On mouse click or hitting the spacebar key: Move up the bird
- If the bird touches a tube: 
    - Catch this event & Quit the game
    - Grey out the display area and display “GameOver”
    - Offer a button “New Game”
- On every passed tube: Count up the score
- The more tubes you pass the more you gain
- On game finish:
    - Store your scores for a player in the frontend:
        - Let the user type in a player name (or offer generation of a random player name)
        - Basic Version: Use LocalStorage to store data
        - Advanced Version: Use IndexedDB to store data


#### Minesweeper
            
Demo: http://minesweeperonline.com/

- Build a UI – build an HTML matrix with 10 x 10 squares (might be an array :))
    - Randomly place 10 bombs inside this matrix (the bombs are hidden)
    - suggestion: use HTML data-attributes to store bomb status in the button
        => research: HTML data-attribute
- Once you start a game: Count the seconds and display them (=game time)
- React to click events on a square
    - On a click: Evaluate if you clicked on a bomb
    - On a right click: Mark a field as a bomb
- If bomb clicked: Game is lost
- If no bomb clicked: Evaluate the “environment”. Do the surroundings have bombs? And how many? Write an algorithm that checks it.
- Bonus:
    - You can play 3 levels: Beginner, Medium, Expert
    - Beginner: generate a matrix of 10 x 10 fields with 10 bombs
    - Medium: generate a matrix of 15 x 15 fields with 40 bombs
    - Expert: generate a matrix of 15 x 30 fields with 100 bombs

---

### Real-Time Applications

For all projects in this category: 
- Research some introduction articles about the concept of WebSockets
- Research the node library: socket.io


#### News Feed

- Create a news application for your favorite interest area
- Project kickoff instructions
    - Create a backend with an HTTP server
        - Create a route which delivers a news item entry form as HTML
        - The form asks for a news category, title and the news message 
        - On entry: Save the news item internally (array + file storage)
        - Emit an event that there is new news, and send the new news item to the event queue
    - Create a UI to display the news
        - Use socket.io to react to new incoming news. Add them in real-time to the DOM (no reload of the page)

#### Chat Application

- Setup a backend server that 
    - listens for chat events (via socket io)
        - a valid chat message must contain: the message and the user who wrote the message
    - forwards / emits incoming chat messages to all users (via socket.io)
        - send the message together with the user who wrote it
- Setup a chat frontend
    - Display all current chat messages via HTML / CSS (e.g. in a textarea)
    - Listen to incoming chat messages via socket io
    - Add new incoming chat message to the chat display area
        - Prefix the message with the user who send the message


---

### Social Media

#### Discussion forum

- You have a main view with discussion topics 
- Each discussion topic can have multiple posts
- And each post can have answers. And these answers can have answers again

Key Concepts to learn:
- Tree structures (=Parents with children, that have children, that have children, etc)
- Practice Algorithm for “looping” through trees: Recursion
- Reading / writing JavaScript data from / to the filesystem

Project kickoff instructions:
- Write a backend that
    - provides an array of topics and all subtopics
    - On load: It reads the topics from a file an loads it into the array 
    - All changes to that arr are again saved to that file
    - Offer a route to fetch a post with all of its subposts
    - Offer a route to receive new incoming discussion entries /answers for a topic / post
        - add the new discussion entry into the topics array / topics file
- Write a frontend that
    - Displays all main topics
    - On click on a topic: show this topic with all sub-threads
    - Indent the sub-answers correctly
        - Use recursion to loop through all posts and subposts, building up the discussion tree
    - Besides each post: Provide a button to reply to it
    - On button click: Forward the user to a post answer page
    - Post answer page: Provide a form to answer the post and a button “Submit answer”

---

### Desktop Applications (Electron)

For all projects: 
- Research the Electron framework
- https://electronjs.org/
- Write your first app: https://electronjs.org/docs/tutorial/first-app

#### Calculator
    - Build a simple calculator app with the basic mathematic operations

#### Rock-Paper-Scissors / Flappy Bird / Minesweeper
    - Implement one of these games as an Electron app


---

## Advanced (long term – 2 weeks up to several months)

### Real Time data

Applications that provide live data in real time (= data in UI is updated very frequently)

#### The Stock trader

- Write an app that displays current DAX Stock prices in real time 
    => the prices can be fake, no need to connect to a real stock price service here
- Key concepts to learn
    - RealTime data with WebSockets / bidirectional data streams
    - Library Socket.io
    - Bonus:
        - Authentication
            - OAuth and Social Login
        - PayPal Payment API
        - Stripe Payment API
- Project kickoff instructions
    - Write a backend which 
        - randomly increases / decreases prices for each stock every second
        - emit an event via socket.io on each price update
    - Write a UI which
        - Fetches and displays all stocks
        - Reacts to price changes and updates the stock items in real time (without any reloads of the page)
    - Bonus: 
        - Backend 
            - maintain customer portfolios of shares
            - add social login (via Facebook, Google or GitHub)
                - suggestion: Start with GitHub social login and research the GitHub documentaiton how to do it
        - UI: 
            - Provide a Login for the user to see his portfolio
            - Portfolio: Allow buying and selling of shares to the current market price
            - Customers have a cash account that is used to order stocks
                - Initialize this cash account with 1000 EUR 
                - On buy / sell: Update the customers cash balance
            - If they do not have enough cash 
                - they need to fill it up with new money from PayPal or Creditcard otherwise they cannot buy stocks anymore
                - The users can state the amount they want to transfer
                - => use the either the PayPal Test API or the Stripe CreditCard Test API for that
                - On successful transaction: Add the amount to the customers cash balance
                - Now they can buy stocks again

---

### Shop / Commercial

Applications with a focus to make money: Shopping carts, ordering process, payment processing.

#### Mini shop with checkout (fullstack)

- You can buy items in a mini shop => you can choose the type of item
- Key concepts to learn / practice:
    - Handling user sessions (= associating data stored on the backend with a user)
    - SessionIDs & Cookies
    - Payment processing / PayPal API
    - Email Sending from the backend
- Project kickoff instructions:
    - Research: Session handling between frontend and node js backend 
    - Backend:
        - Provide a POST route /cart/add
        - The route receives a product in the request body
        - On call: 
            - Fetch the product item from the POST body
            - Add item to a shopping cart object
            - Store the received shopping cart items of every user (either in variables or in files)
            - If there is no session ID in the cart object
                - Generate a unique session ID (use UUID package for that)
                - Send it to the client as Cookie => research how to do that
    - Frontend
        - Provide a UI which lists all of your products.
        - Pick images for your products from a free image source: pixabay, unsplash, etc
        - Ideally your product information comes from the backend. Fetch it via fetch() from the backend
        - For each product: Provide a buy button
        - On “buy Product” click: Call the route product/add
        - Store the returned session ID in a cookie => research how to do that with JavaScript
            - If there is already a session ID in the browser: do not add it
        - After the backend responded => forward the user to a shopping cart page
        - Provide a Shopping cart page
            - List all your bought products with quantity, price, item total price and cart total price
            - Provide a button “Checkout” which leads you to the checkout page
    - Checkout page: 
        - UI: Fill out customer address and delivery address
        - Provide a button “Continue with payment”
        - On click
            - Send the address to the backend
            - Backend: Store this information in the shopping cart object on the server
        - Forward the user to the payment processing page
    - Process a paypal payment
        - Provide a page where the user sees the total sum to pay and a button “Pay with paypal”
        - Register a paypal developer account
        - Use the PayPal test API to make test transactions 
        - => research how to set this up in the paypal developer documentation
        - After paypal responded with a success of the transaction => forward user to order confirmation
    - Send Order confirmation
        - Send the customer an email with his order id, a summary of the ordered products, the calculated sum, his address and a “widerrufsrecht” (revocation notice)
        - Email server setup
            - Install an SMTP client for sending emails from your system
            - Recommendation for an easy setup: ssmtp or msmtp
        - BONUS: Also send a SMS to the user
            - Research SMS APIs which provide some rate of free SMS sending
            - Send a SMS order confirmation to the users phone number

---

### Streaming

#### Video course

- Produce a small video course of 5-10 videos
    - Shoot some videos with your smartphone camera, photo camera laptop webcam
    - These videos do not really need to have serious course content. But it is a good side-learning to try out for practicing presenting skills, a skill you could really benefit from a lot in your career if you practice it
- Key Concepts to practice: 
    - The Video tag in HTML5
    - NodeJS streams
    - HTTP partly responses => range header
    - Authentication with JSON Web Tokens
    - BONUS: Presentation skills
- Project kickoff instructions
    - Create a UI
        - Login UI with email and password
        - Video course page listing all videos of the course
        - Video view page where you can watch a single video
            - This page should contain a HTML5 video player (use the HTML \<video\> tag)
        - Serve all this UIs via a NodeJS HTTP or Express HTTP server
        - => Recommendation: HTTP server to really learn the fundamentals of frontend-	backend interaction
        - => Express is much easier in the long-run. But you have to learn it first
    - Create a backend video server
        - Store your videos in a course folder
        - Provide a route which returns the video player UI page
        - Provide a route which accepts a video ID and streams back the video with this ID
    - Add authentication
        - Add JWT (JSON Web Token) authentication to your project
            - => research this topic
        - On each request to your backend (except the login route): 
            - Check if the HTTP header “Authorization” is present
            - If not this means: the user is not logged in and we deny the request
            - Not logged in users are always redirected back to the route /login
            - If you are using express: 
                - use a middleware for that auth check
                - => Research how to inject a middleware function on each incoming request
                - If your are not using express: 
                    - Write a function for the auth check which is executed on every incoming request. Research how to do that
        - Provide a route on the backend to authenticate a user by email and password
            - Check the user credentials against an array of users
            - If user email and password is correct => create a JSON web token
            - => research how to do this in NodeJS (you need to install a package for that)
            - Return back the JSON web token
        - Frontend adaptation
            - The login frontend form 
                - After submit the form needs to wait for the auth on the backend to finish
                - Afterwards it will store the received token in localStorage
                - => research what browser LocalStorage is and how to store data in the browser

---

### Mobile app development

Learn how to create native web applications for the smartphone.

    - Develop an app with React Native or Google Flutter
        - For each app idea: Follow either...
            - a React native introduction course
            - a Flutter introduction course
            - or read the documentation on these and code your first hello world application by the guides from the official docs
            => decide afterwards what you find more appealing to code

    - Concepts to learn:
        - Design UIs for mobile
        - Use native mobile controls
        - Mobile payment processing
        - React specific
            - Convert a react app to a mobile app
             
#### Pizza Order App

    - Create an app for choosing pizza
        - you can choose a standard pizza or
        - you can add extras to the pizza
    - Ordering of the pizza
        - provide a delivery address and phone number
    - Advanced: Build an order backend
        - Payment processing on a mobile app 
            - => use the PayPal Test API
        - Send an Email with the pizza order confirmation


---

### Desktop Applications with Electron

For all projects: 
- Research the Electron framework
- https://electronjs.org/
- Write your first app to learn the fundamentals: https://electronjs.org/docs/tutorial/first-app

Motivation for desktop apps: 
- Very fast / high performance
- Access your computer resources, e.g. files, folders 
- Do not share data over the internet (=keep it outside of the web)
    => e.g. handling private journals or very confidential stuff like passwords, financial data, etc
        
#### Task Manager

- Write a program that simulates the Windows Task Manager in Linux
- Show the running applications / processes and how much of the computer resources (CPU / RAM) they currently consume
- Concepts to learn: Unix processes and computer resource usage information


#### Password / Credentials Bookkeeper

- Create an app which stores all your logins for all the pages you use
- Create a strong master password which is needed to access your login data
- After login you can see the list of your login accounts
- Provide a possibility to add a new page with login information


---

### Software Deployment with Docker

- Docker is the de facto standard of deploying software together with its environment on a server
    - e.g. install your node js application together with node and mongoDB out-of-the-box
    - or install your wordpress blog together with PHP and MySQL out-of-the-box
    => this (almost) assures your software will run everywhere like it runs on your local PC
- Install Docker: https://phoenixnap.com/kb/how-to-install-docker-on-ubuntu-18-04
- Full introduction course (quite long): https://www.youtube.com/watch?v=fqMOX6JJhGo
    - You can also start off by reading the official docks instead of a course
- Run your first hello world container
- Demo - Setup wordpress
    - Install wordpress from the official docker image
    - Startup your wordpress blog in a local server + database
- Learn about Docker Images and the central         Docker Image Repository
