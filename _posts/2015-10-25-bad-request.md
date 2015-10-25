---
published: true
---


## 400 Bad Request

In a new node.js Express project, I kept getting a 400 - Bad Request response from the Passport-Local module. This didn't make sense to me, and I couldn't figure out why it was happening.

I checked the input names on the form. I checked the options on the passport strategy. I finally ended up tracing into the passport code in node_modules and found that `req.body` was empty.

The source of the problem was that I hadn't used `bodyParser.urlencoded` in my app. I had used `bodyParser.json` but that didn't work for form data from my login form.

How many hours did I spend on that error?
