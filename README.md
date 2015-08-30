# fetch-tweets
> A simple to use, feature-rich, tested node module for fetching Tweets from the Twitter API.

## Set up

```npm install fetch-tweets --save```

Include the following code in your file. 
This includes the fetch-tweets module, creates a new instance and passes in your Twitter API keys.
```
var FetchTweets = require('fetch-tweets'); // Include the module

// Specify Twitter keys (preferably in an external .gitignore'd file)
apiKeys = {
    consumer_key : 'XXXXXXXXXXXXXXXXXXXXXXXXX',
    consumer_secret : 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'
};

// Create a new object and pass in keys and optional additional options (see below)
var fetchTweets = new FetchTweets(apiKeys); 
```

## Selecting Tweets by keyword(s)
There are two methods of selecting Tweets by keyword, using Twitter search API. 
* Single paramater string containing the search term
* Single paramater JSON object containing options
### Simple example
```
fetchTweets.byTopic('JavaScript', function(results){
   console.log(results); // Do whatever with the results
});
```
There are a series query operators that can be used inside this string parameter, such as fetching Tweets containg multiple keywords. To view a list of query operators click here.

### Searching with more options
You can also search for Tweets by passing in a JSON object containing options set by the Twitter API. There is an extensive list of options such as dates, locations, languages and popularity. For example:

```
var options = {
  q: 'banana',
  lang: 'en',
  result_type: 'popular',
  count: 5,
}

fetchTweets.byTopic(options, function(results){
   console.log(results); // Do whatever with the results
});
```

## The Results
There are two options for how you'd like your results returned:
* Formated Results - just the useful stuff *(default)*
* Full Results - exactley what is returned by the Twitter API

### Formated Results (just the usefull stuff)
This is default, so you don't need to do anything different than above
Results will be returned in the following format:
```
[
    {   date: 'Sun Aug 30 15:55:09 +0000 2015',
        body: 'JavaScript is just so totally awesome',
        location: { geo: null, coordinates: null, place: null },
        'retweet-count': 23952,
        'favorited-count': 0,
        lang: 'en' },
    {   date: 'Sun Aug 30 15:55:09 +0000 2015',
        body: 'Ony one thing more awesome than JavaScript and that's CoffeeScript!!',
        location: { geo: null, coordinates: null, place: null },
        'retweet-count': 0,
        'favorited-count': 0,
        lang: 'en' },
    {   date: 'Sun Aug 30 15:55:08 +0000 2015',
        body: 'And the one thing more awesome than CoffeeScript, Coffee!!!!',
        location: { geo: null, coordinates: null, place: null },
        'retweet-count': 0,
        'favorited-count': 0,
        lang: 'en'
    }
]
```


### Full Results
If you would like the full results returned by the Twitter API, then you can specify the second parameter as false when creating the fetchTweets object:
```
var FetchTweets = require('fetch-tweets');
var fetchTweets = new FetchTweets(apiKeys, false);
```

You can view an example of the format of these results [here, on the Twitter website](https://dev.twitter.com/rest/reference/get/search/tweets)

License
----
MIT




