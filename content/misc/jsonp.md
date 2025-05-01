---
title: JSONP - A weird way of transferring data
---
### ⚠️DISCLAIMER
Contents of this article might fall into a grey area from legal standpoint (I feel), hence I do not take any responsibility if you get into any legal troubles. All this is solely for educational purposes.
### JSONP, huh?
So you must have heard about JSON or JavaScript Object Notation, a pretty common and popular way of information exchange between two applications, processes or whatever, and is pretty much human-readable. But what is JSONP? A quick Google search reveals the name expands to `JSON with Padding`, which, in my opinion is a naming blunder as there is NOTHING, literally NOTHING related to padding over here.
### Cut the bullshit, get to the point
So I encountered this abnormal style of data transfer while working on a task given by a firm as an assessment round. I had to scrape data off the official website of IPL, which is [iplt20.com](https://www.iplt20.com/), but it was too difficult to scrape content as they have dynamic content which is loaded only after the JavaScript gets loaded on the page.

This means JS modules like [cheerio](https://cheerio.js.org/) were not able to scrape the data as they don't execute the JS that is present on the HTML DOM. I tried with [puppeteer](https://pptr.dev/) as well to emulate a headless browser but I had a lot (like really a lot) of trouble running it inside a docker container (yes I was doing it in a way that I could deploy it anywhere).

So after wasting 2 days of my precious weekend over scraping, I decided to give up (no, not the task, but the approach). I then decided to dig deep into the website's sources, how they were transferring data and loading match details, and how were they updating it in real time
### Okay enough, can you please tell about JSONP, PLEASE!
**TL;DR** Here's a [wikipedia article](https://en.wikipedia.org/wiki/JSONP) that will tell you almost everything

So for those who want to continue further, here is the thing: JSONP is essentially a JS function call that has arguments inside it. Simply speaking, if the endpoint `http://server.example.com/Users/1234` intends to return a JSON object like this:
```json
{
    "Name": "Clem",
    "Id": 1234,
    "Rank": 7
}
```
It would instead return a function call that can be used by the client side JavaScript. So the returned response would look like this:
```js
parseResponse({"Name": "Clem", "Id": 1234, "Rank": 7});
```
Now how is this useful? Well I don't know honestly. I just did the research required to fulfil the objectives of the task. Maybe this helps to 'couple' the UI well with the server and to prevent anyone from directly hitting the API and getting the JSON result in a pure format. Whatever be the case, I feel this standard is kinda awkward to work with.
### So what did you do then?
Well, since JSONP response is a function call essentially, which implies that if I write the same function on my end, it can be evaluated as I wish it to be. And it worked, here's how:
- I first identified the APIs which were returning the data I needed in a structured format. One of them was as follows:
```text
https://ipl-stats-sports-mechanic.s3.ap-south-1.amazonaws.com/ipl/feeds/stats/203-groupstandings.js?ongroupstandings=_jqjsp&_1745578746203=
```
-  The response upon hitting this URL was like follows (truncated the response as it was too long):
```javascript
ongroupstandings({
    "category":null,
    "points":[
        {
            "StandingFlag":"NET",
            "Category":null,
            "CompetitionID":"203",
            "TeamID":"35",
            "TeamCode":"GT",
            "TeamName":"Gujarat Titans",
            "TeamLogo":"https:\/\/scores.iplt20.com\/ipl\/teamlogos\/GT.png?v=1",
            "Matches":"8",
            "Wins":"6",
            "Loss":"2",
            "Tied":"0",
            "NoResult":"0",
            "Points":"12",
            "Draw":"0",
            "ForTeams":"1550\/153.5",
            "AgainstTeam":"1431\/159.3",
            "NetRunRate":"1.104",
            "Quotient":"1.715",
            "OrderNo":"1",
            "IsQualified":null,
            "LeadBy":"0",
            "Deficit":"0",
            "Performance":"W,W,L,W,W",
            "Status":"SAME",
            "MATCH_ID":"1839",
            "PrevPosition":"1"
        }
    ]}
);
```
- This was the response for the points table. Now each entry in the `points` array denoted one position, and it had all the data that I needed. So in order to access the data, all I did was to take the response, pass it into an `eval` (I know it's unsafe, will come back to it later), and defined my own `ongroupstandings` function.
- When my `ongroupstandings` function executed, I stored the value passed into it in a global variable, and hence the standard JSON data was available to me, now in a proper JavaScript Object. Yay!
### Talk is cheap, show me the code
- Okay fine, here you go. Following is a snippet that would work in Node.js:
```javascript
const URL = 'https://ipl-stats-sports-mechanic.s3.ap-south-1.amazonaws.com/ipl/feeds/stats/203-groupstandings.js';
let res = null;

function ongroupstandings(data) {
    res = data;
}

async function main() {
    try {
        const response = await fetch(URL);
        const result = await response.text();
        eval(result); // This will trigger execution of our function
        console.log(res);
    } catch (error) {
        console.log("An error occured", error);
    }
}

main();
```
- And this would work in your browser:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <code id="root"></code>
    <script>
        function ongroupstandings(data) {
            // do anything with the data here, like show in body
            document.getElementById("root").innerText = JSON.stringify(data);
        }
    </script>
    <script src="https://ipl-stats-sports-mechanic.s3.ap-south-1.amazonaws.com/ipl/feeds/stats/203-groupstandings.js"></script>
</body>
</html>
```
- Here we are simply including the JSONP callback as `JavaScript code` in our DOM. When the browser parses the HTML, during the execution of the code in `<script>` tags, first the function is defined, and then the foreign script is included.
- This runs the callback which comes as a response in the browser, the JS function which we defined already gets executed, and the data is available to us for use. In this example I just simply append it to the existing HTML.
- The output looks as follows:
![[ipl-jsonp-output.png]]
### Well, interesting, but what about `eval()`?
- The `eval()` function is considered to be unsafe in JavaScript as it can open up your code to injection attacks. However, as I'm NOT passing any user input in `eval()` and since the JSONP callback string is being trusted by the official IPL website, I guess I can trust it too.
- There might be some other way to safely execute the JSONP callback, but I'm not aware of it. For now my purpose is fulfilled, and I'm happy with it. Moreover the API call is being done from my backend server, so it is unlikely that any injection attack can be done on it as I'm not exposing any endpoint which will utilise the `eval()` for processing other than getting data from these API endpoints
### Can I try this at home?
- Sure, go ahead and get your hands dirty :)
- Build your own applications on top of these APIs. Just dig through the browser's console properly. Since the data is in public domain, I don't think there is any legal issue involved.
- However, if the traffic goes unexpectedly high on the IPL's AWS, they might implement some techniques to circumvent the usage of these APIs by third parties like us.