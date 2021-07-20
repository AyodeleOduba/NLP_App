## About project
This project relies on Meaningcloud which is a software as a service product that enables users to embed text analytics and semantic processing in any application or system. It was previously described as Textalytics. Semantic Meaning extends the concept of semantic API with a cloud-based framework that makes integrating semantic processing into any system akin to a plug-and-play experience.
We will use it to bring back each of our subjectivity, confidence, irony, score_tag and agreement to the user.
Only the user has to submit URL article.

## Tech used
Initially, I used a function to check if it is an the input url or not 
```javaScript
if (Client.isValid(formText)) {
        Client.requestAPI(formText)
        console.log("::: Form Sent :::")
    } else {
        alert("Please enter a valid URL.")
    }
```
Then I used the url and API Keys of Meaningcloud to access the required data
```javaScript
var data = qs.stringify({
    key: process.env.API_KEY,
    lang: 'en',
    txt: 'API',
    url: req.body.mysite,
  });
  var config = {
    method: 'post',
    url: 'https://api.meaningcloud.com/sentiment-2.1',
    headers: {
      'Content-Type': 'application/x-www-form-urlencoded',
      Cookie: 'PHPSESSID=n5vopf997smdtu0ergefsrp0ch',
    },
    data: data,
  };
```
Finally, on updateUI, I returned the data to the user
```javaScript
export const updateUI = (myData) => {
  document.getElementById(
    'score_tag'
  ).innerHTML = `score_tag:  ${myData.score_tag}`;
//...
};
```