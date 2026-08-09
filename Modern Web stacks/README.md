This lab is a summary of what I learned from the modern web stacks room from tryhackme.

1. MERN applications. These contain MongoDB, express, react, and node.js. The flow goes like this from browser to server.
   Node.js - a client-side uses js to process button clicks and interactive stuff, while this is the javascript that the server uses to process the browsers' http requests. For example, a user makes a GET\profile request, that request is sent to the server, server uses node.js to process the request and build a reply.
   Express - Used to help node.js in processing requests, it makes building responses way more efficient.
   MongoDB - the database that stores persistent data, could be user submitting POST or applications submitting POST.
   React - the displayed html code that the client sees, html is the entire thing like the structure, while react is what displays parts of it instead of directing you to another html file or page.
This framework or structure is commonly used since it mainly uses javascript which makes it easier for developers. Nginx can be used as reverse proxy which means requests go to nginx on port 80 or 443 instead of express port 3000. This provides security since it prevents backend access. If not configured, then express will be left exposed meaning exposed backend.

2. when looking at curl results, check for the header to see what the backend is using. in this case, powered by:express is shown. Meaning if u dont see that header then most likely its not using express or its being stripped by nginx.
3. another is the cookie ID. You can see the cookie source, in this case its connect.sid which is commonly used in express-session which is another clue that makes it stronger that express is being used. though absence of connect.sid doesnt mean absence of express.
4. you can also try curl without the -I and some nonexistent route and if server uses express, its gonna show Cannot GET /nonexistent
5. 
6. 
