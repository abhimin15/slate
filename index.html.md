--- 

title: ParallelDots Text API

language_tabs: 
   - shell 
   - ruby
   - python
   - java
   - php
   - csharp
   - r
toc_footers: 
   - <a href='https://www.paralleldots.com/sign-up'>Sign Up for a Developer Key</a>

includes: 
   - errors 

search: true 

--- 

# Introduction 

AI Powered Text Analysis Apis  

**Version:** 4.0

#Installation

For setup and installation instruction, please visit our <a href="https://github.com/paralleldots"> Github Page </a>. Specifically, below are the links to each of our Client Libraries:

-<a href="https://github.com/ParallelDots/ParallelDots-Csharp-API">C#</a><br>
-<a href="https://github.com/ParallelDots/ParallelDots-Java-API">Java</a><br>
-<a href="https://github.com/ParallelDots/ParallelDots-Python-API">Python</a><br>
-<a href="https://github.com/ParallelDots/ParallelDots-PHP-API">PHP</a><br>
-<a href="https://github.com/ParallelDots/ParallelDots-ruby-API">Ruby</a><br>
-<a href="https://github.com/ParallelDots/ParallelDots-R-API">R</a>

```ruby
From Gem:

gem install paralleldots
```

```python
From PyPI:
pip install paralleldots

From Source:
https://github.com/ParallelDots/ParallelDots-Python-API.git
python setup.py install

```



```java

Use the JAR
paralleldots-1.0.1.jar
Path to JAR
path: target/paralleldots-1.0.1.jar

Dependencies
okhttp-3.10.0.jar
okio-1.14.0.jar
json-simple-1.1.jar
```

```php
1.Create a composer.json file in your project's directory.

2.Write the following in the file:
{
  "require": {
    "paralleldots/apis": "*"
  },
  "minimum-stability": "dev"
}
3.Run the following command in the same directory (NOTE: You must have composer installed):"

composer install

```
```csharp
Open the console in Visual Studio using the Tools > NuGet Package Manager > Package Manager Console command.

PM> Install-Package ParallelDots

```

```r
library("devtools")
devtools::install(<path_to_locally_cloned_repo>)

Dependencies:
httr
jsonlite

```






# List of Supported Languages with their Language Codes

- Portuguese(pt)
- Simplified Chinese(Not available in multilingual keyword generator API) (zh)
- Spanish(es)
- German(de)
- French(fr)
- Dutch(nl)
- Italian(it)
- Japanese(ja)
- Thai(th)
- Danish(da)
- Finnish(fi)
- Greek(el)
- Russian(ru)
- Arabic(ar)



> Make sure to replace `xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx` with your API key.

ParallelDots Text Analytics APIs uses an API key to authenticate requests to the API. Please pass your API key as a parameter (api_key) in each of our APIs to authenticate requests.

You can register for a new API key by signing up for a [ParallelDots account](https://www.paralleldots.com/sign-up).

<aside class="notice">
You must replace <code>xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx</code> with your own API key.
</aside>

# /SENTIMENT
## ***POST*** 

**Summary:** Find the overall sentiment of a block of text along with the confidence score.

**Description:** Sentiment API accepts two parameters - text and api_key and returns a json response containing the overall sentiment of the input text and confidence score for each of the sentiment label (positive, negative and neutral). There is no limitation to the number of characters that you can pass to the API but for optimum results, please pass short texts (tweets, comments, news headlines, etc.)

```ruby
require 'paralleldots'

set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

# for single sentence

text="Come on, lets play together"
puts( sentiment(text))


# for multiple sentence as array
text_array = ["Come on,lets play together","Team performed well overall."]
puts(batch_sentiment(text_array))



```

```python
import paralleldots
paralleldots.set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")


# for single sentence
text="Come on, lets play together"
lang_code="en"
response=paralleldots.sentiment(text,lang_code)
print(response)

# for multiple sentence as array
text=["Come on,lets play together","Team performed well overall."]
response=paralleldots.batch_sentiment(text)
print(response)

```

```shell
# For single sentence

curl -X POST -F 'text=Come on, lets play together' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/sentiment

# for multiple sentence as array

curl -X POST -F 'text=["Come on,lets play together","Team performed well overall."]' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/sentiment_batch
```

```java
import com.paralleldots.paralleldots.App;
import org.json.simple.JSONObject;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;


App pd = new App("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");
// for single sentences
    String sentiment = pd.sentiment("Come on, lets play together");
    System.out.println(sentiment);

// for multiple sentence as array
    JSONArray text_list = (JSONArray)parser.parse("[ \"Come on, lets play together\",\"Team performed well overall\" ]");
    String sentiment_batch = pd.sentiment_batch(text_list);
    System.out.println(sentiment_batch);
```

```php
<?php
require(__DIR__ . '/vendor/paralleldots/apis/autoload.php');
set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"); 

# for single sentence 
echo sentiment("Come on, lets play together");

# for multiple sentence as array

$text_list = "[ \"Come on, lets play together\",\"Team performed well overall\" ]";
echo sentiment_batch($text_list);
?>
```

```csharp
using ParallelDots

// Initialize instance of api class
paralleldots pd = new paralleldots("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");


// for single sentence
String sentiment = pd.sentiment("Come on, lets play together");
Console.WriteLine(sentiment);
// for multiple sentence as array
JArray text_list = JArray.Parse("[\"Come on,lets play together\",  \"Team performed well overall.\"]");
String sentiment_batch = pd.sentiment_batch(text_list);
Console.WriteLine(sentiment_batch);



```

```r
# for single sentence

url="https://apis.paralleldots.com/v4/sentiment"
text="Come on lets play together"
lang_code='en'
result<-sentiment(url,text,api_key,lang_code)
print(result)	

# for multiple sentence

url="https://apis.paralleldots.com/v4/sentiment_batch"
text='["Come on lets play together","Team performed well overall"]'
lang_code='en'
result<-sentiment(url,text,api_key,lang_code)
print(result)	
```




> The above command returns JSON structured like this:

```json
{
    "sentiment": {
        "negative": 0.013,
        "neutral": 0.891,
        "positive": 0.096
    }
}

Batch Output -

{
    "sentiment": [
        {
            "negative": 0.013,
            "neutral": 0.891,
            "positive": 0.096
        },
        {
            "negative": 0.002,
            "neutral": 0.02,
            "positive": 0.978
        }
    ]
}
```

### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/sentiment

`***POST*** /sentiment` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text | query | Pass a short statement/multiple statement in case of batch  | Yes | string/array |
| api_key | query | Your API key | Yes | string |
| lang_code | query | Language Code | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| sentiment | Type of sentiment present in text i.e (positive,neutral,negative) | object |
| probabilities | The confidence score of each of the sentiment. It lies between 0 to 1 . Higher score states the higher confidence score of the output.| float |

**HTTP Error Codes**

| Code | Text | Description |
| ---- | ---- | ----------- |
| 200 |OK| Successful response |
| 304 |Not Modified| There was no new text to return. |
| 500 |Internal Server Error| Backend Error. |
| 400 |Bad Request| Please provide valid input parameter. |
| 401 |Unauthorized| Invalid Credentials. Please provide valid API key |
| 403 |Forbidden| Daily/Monthy Limit Exceeded. Please upgrade your account from your user dashboard at <a href="https://user.apis.paralleldots.com/user_dashboard">https://user.apis.paralleldots.com/user_dashboard</a>  |
| 429 |Too Many Requests| Please wait for sometime before making further API calls |
| 406 |Not Acceptable| Invalid Format for any of the parameters. For e.g.:sending api_key as integer instead of string. |


# /SIMILARITY
## ***POST*** 

**Summary:** Find similarity between two snippets of text. 

**Description:** Semantic Analysis API accepts three parameters - text_1, text_2 and api_key which are two snippets of text and the API returns a json response with an actual score (between 0 and 1) and normalized score (between 0 and 5). Please ensure there are at least **two words** in each of the text_1 and text_2 sentences otherwise the API will return an error.

```ruby
require 'paralleldots'

set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

text1="There is a tipping point’: UN warns climate change goals laid out in Paris accord are almost out of reach"
text2="Global warming set to exceed Paris agreement’s 1.5C limit by 2040s, according to draft UN report"
puts(similarity(text1,text2))

```

```python
import paralleldots
paralleldots.set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")
text1="There is a tipping point’: UN warns climate change goals laid out in Paris accord are almost out of reach"
text2="Global warming set to exceed Paris agreement’s 1.5C limit by 2040s, according to draft UN report"
response=paralleldots.similarity(text1,text2)
print(response)

```

```shell
curl -X POST -F "text_1=There is a tipping point’: UN warns climate change goals laid out in Paris accord are almost out of reach" -F "text_2=Global warming set to exceed Paris agreement’s 1.5C limit by 2040s, according to draft UN report" -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/similarity


```


```java
import com.paralleldots.paralleldots.App;
import org.json.simple.JSONObject;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;
App pd = new App("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

    String similarity = pd.similarity("There is a tipping point’: UN warns climate change goals laid out in Paris accord are almost out of reach", "Global warming set to exceed Paris agreement’s 1.5C limit by 2040s, according to draft UN report");
    System.out.println(similarity);

    
```

```php
<?php
require(__DIR__ . '/vendor/paralleldots/apis/autoload.php');
set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"); 

echo similarity("There is a tipping point:UN warns climate change goals laid out in Paris accord are almost out of reach", "Global warming set to exceed Paris agreement’s 1.5C limit by 2040s, according to draft UN report");
?>

```

```csharp
using ParallelDots

// Initialize instance of api class
paralleldots pd = new paralleldots("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

String similarity = pd.similarity("There is a tipping point: UN warns climate change goals laid out in Paris accord are almost out of reach", "Global warming set to exceed Paris agreement’s 1.5C limit by 2040s, according to draft UN report");
Console.WriteLine(similarity);


```


```r

url="https://apis.paralleldots.com/v4/similarity"
text="There is a tipping point’: UN warns climate change goals laid out in Paris accord are almost out of reach"
text2="Global warming set to exceed Paris agreement’s 1.5C limit by 2040s, according to draft UN report"
result<-similarity(url,text1,text2,api_key)
print(result)

```

> The above command returns JSON structured like this:

```json
{
    "similarity_score": 0.6146203876
}
```

### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/similarity

`***POST*** /similarity` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text_1 | query | Pass a long statement (at least two words)| Yes | string |
| text_2 | query | Pass a long statement (at least two words) | Yes | string |
| api_key | query | Apikey | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| actual_score | The normalized score of each of the sentiment. It lies between 0 to 1 . Higher score states the higher confidence score of the output.| float |
| normalized_score | The normalized score of each of the sentiment. It lies between 0 to 5 . Higher score states the higher confidence score of the output.| float |

**HTTP Error Codes**

| Code | Text | Description |
| ---- | ---- | ----------- |
| 200 |OK| Successful response |
| 304 |Not Modified| There was no new text to return. |
| 500 |Internal Server Error| Backend Error. |
| 400 |Bad Request| Please provide valid input parameter. |
| 401 |Unauthorized| Invalid Credentials. Please provide valid API key |
| 403 |Forbidden| Daily/Monthy Limit Exceeded. Please upgrade your account from your user dashboard at <a href="https://user.apis.paralleldots.com/user_dashboard">https://user.apis.paralleldots.com/user_dashboard</a>  |
| 429 |Too Many Requests| Too Many Requests. Please try after sometime. |
| 406 |Not Acceptable| Invalid Format. Parameter text should be string |

# /NER
## ***POST*** 

**Summary:** Named Entitiy Extraction

**Description:** Named-entity recognition (NER) can identify individuals, companies, places, organization, cities and other Stringious type of entities. The API accepts text, lang_code and api_key as three parameters and returns a json with the entities, their category (name, place or organization) and confidence scores. 
NER API is available in English, Spanish(es), Dutch(nl) and German(de) languages. To use the NER API in laguages other than English please pass an extra parameter in the form of lang_code.

```ruby
require 'paralleldots'

set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

# for single sentence
text="Apple was founded by Steve Jobs."
lang_code="en"
puts(ner(text,lang_code))


# for multiple  sentence as array
text_array = ["Apple was founded by Steve Jobs.","Apple Inc. is an American multinational technology company headquartered in Cupertino, California"]
puts(batch_ner(text_array))



```

```python
import paralleldots
paralleldots.set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

# For single sentence
text="Apple was founded by Steve Jobs."
lang_code="en"
response=paralleldots.ner(text,lang_code)
print(response)

# for multiple sentence as array
text=["Apple was founded by Steve Jobs.","Apple Inc. is an American multinational technology company headquartered in Cupertino, California"]
response=paralleldots.batch_ner(text)
print(response)


```

```shell
# For single sentence

curl -X POST -F 'text=Apple was founded by Steve Jobs.' -F 'lang_code=en' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/ner

# for multiple sentence as array

curl -X POST -F 'text=["Apple was founded by Steve Jobs.","Apple Inc. is an American multinational technology company headquartered in Cupertino, California"]'  -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/ner_batch
```

```java
import com.paralleldots.paralleldots.App;
import org.json.simple.JSONObject;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;
App pd = new App("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

// for single sentences
    String ner = pd.ner("Apple was founded by Steve Jobs.","en");
    System.out.println(ner);
// for multiple sentence as array
    
    JSONArray text_list = (JSONArray)parser.parse("[ \"Apple was founded by Steve Jobs\", \"Apple Inc. is an American multinational technology company headquartered in Cupertino.\"]");
    
    String ner_batch = pd.ner_batch(text_list);
    System.out.println(ner_batch);
  
```

```php
<?php
require(__DIR__ . '/vendor/paralleldots/apis/autoload.php');
set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"); 

# for single sentences

echo ner("Apple was founded by Steve Jobs","en");

# for multiple sentences as array.
$text_list = "[ \"Apple was founded by Steve Jobs\", \"Apple Inc. is an American multinational technology company headquartered in Cupertino.\"]";
echo ner_batch($text_list);

?>

```

```csharp
using ParallelDots

// Initialize instance of api class
paralleldots pd = new paralleldots("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");


// for single sentences
String ner = pd.ner("Apple was founded by Steve Jobs","en");
Console.WriteLine(ner);

v
// for multiple sentences as array.

JArray text_list = JArray.Parse("[\"Apple was founded by Steve Jobs\", \"Apple Inc. is an American multinational technology company headquartered in Cupertino, California\"]");

String ner_batch = pd.ner_batch(text_list);
Console.WriteLine(ner_batch);

```

```r
# for single sentence

url="https://apis.paralleldots.com/v4/ner"
text="Apple was founded by Steve Jobs."
lang_code = "en"
result<-ner(url,text,lang_code,api_key)
print(result)

# for multiple sentence

url="https://apis.paralleldots.com/v4/ner_batch"
text='["Apple was founded by Steve Jobs","Apple Inc. is an American multinational technology company headquartered in Cupertino."]'
result<-ner(url,text,api_key)
print(result)
```

> The above command returns JSON structured like this:

```json
[
    {
        "name": "Apple",
        "category": "group",
        "confidence_score": 0.9998493195
    },
    {
        "name": "Steve Jobs",
        "category": "name",
        "confidence_score": 0.9928660691
    }
]
Batch Output -

{
    "entities": [
        [
            {
                "name": "Apple",
                "category": "group",
                "confidence_score": 0.466986
            },
            {
                "name": "Steve Jobs",
                "category": "name",
                "confidence_score": 0.893464
            }
        ],
        [
            {
                "name": "Apple Inc",
                "category": "group",
                "confidence_score": 0.751582
            },
            {
                "name": "California",
                "category": "place",
                "confidence_score": 0.908735
            }
        ]
    ]
}

```

### HTTP Request

**Endpoint** https://apis.paralleldots.com/v4/ner

`***POST*** /ner` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text | query | Pass a long statement/multiple statement in case of batch | Yes | string/array |
| api_key | query | Apikey | Yes | string |
| lang_code | query | Language Code | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| entities | Contains all the entities and their corresponding type and confidence_score | array | 
| category | Name of the type of entity. | string |
| name | Name of the entity. | string |
| confidence_score | The confidence score of the entity in the text. It lies between 0 to 1 . | float |

**HTTP Error Codes**

| Code | Text | Description |
| ---- | ---- | ----------- |
| 200 |OK| Successful response |
| 304 |Not Modified| There was no new text to return. |
| 500 |Internal Server Error| Backend Error. |
| 400 |Bad Request| Please provide valid input parameter. |
| 401 |Unauthorized| Invalid Credentials. Please provide valid API key |
| 403 |Forbidden| Daily/Monthy Limit Exceeded. Please upgrade your account from your user dashboard at <a href="https://user.apis.paralleldots.com/user_dashboard">https://user.apis.paralleldots.com/user_dashboard</a>  |
| 429 |Too Many Requests| Too Many Requests. Please try after sometime. |
| 406 |Not Acceptable| Invalid Format. e.g: Parameter text should be string |

# /TAXONOMY
## ***POST*** 

**Summary:** Classify content into IAB categories

**Description:** Taxonomy API accepts two parameters - text and api_key and returns a json containing an array of top 3 categories that matches the input text. 

```ruby
require 'paralleldots'

set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

# for single sentence
text="Apple was founded by Steve Jobs."
puts(taxonomy(text))


# for multiple  sentence as array
text_array = ["Apple was founded by Steve Jobs.","Apple Inc. is an American multinational technology company headquartered in Cupertino, California"]
puts(batch_taxonomy(text_array))



```

```python
import paralleldots
paralleldots.set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

# For single sentence
text="Apple was founded by Steve Jobs."
response=paralleldots.taxonomy(text)
print(response)

# for multiple sentence as array
text=["Apple was founded by Steve Jobs.","Apple Inc. is an American multinational technology company headquartered in Cupertino, California"]
response=paralleldots.batch_taxonomy(text)
print(response)


```

```shell
# For single sentence

curl -X POST -F 'text=Apple was founded by Steve Jobs.' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/taxonomy

# for multiple sentence as array

curl -X POST -F 'text=["Apple was founded by Steve Jobs.","Apple Inc. is an American multinational technology company headquartered in Cupertino, California"]' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/taxonomy_batch
```

```java
import com.paralleldots.paralleldots.App;
import org.json.simple.JSONObject;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;
App pd = new App("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

// for single sentences
    String taxonomy = pd.taxonomy("Apple was founded by Steve Jobs.");
    System.out.println(taxonomy);
// for multiple sentence as array
    
    JSONArray text_list = (JSONArray)parser.parse("[ \"Apple was founded by Steve Jobs\", \"Apple Inc. is an American multinational technology company headquartered in Cupertino.\"]");

    String taxonomy_batch = pd.taxonomy_batch(text_list);
    System.out.println(taxonomy_batch);
  
```

```php
<?php
require(__DIR__ . '/vendor/paralleldots/apis/autoload.php');
set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"); 

# for single sentences

echo taxonomy("Apple was founded by Steve Jobs");

# for multiple sentences as array.
$text_list = "[ \"Apple was founded by Steve Jobs\", \"Apple Inc. is an American multinational technology company headquartered in Cupertino.\"]";
echo taxonomy_batch($text_list);

?>

```

```csharp
using ParallelDots

// Initialize instance of api class
paralleldots pd = new paralleldots("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");


// for single sentences
String taxonomy = pd.taxonomy("Apple was founded by Steve Jobs");
Console.WriteLine(taxonomy);

v
// for multiple sentences as array.

JArray text_list = JArray.Parse("[\"Apple was founded by Steve Jobs\", \"Apple Inc. is an American multinational technology company headquartered in Cupertino, California\"]");

String taxonomy_batch = pd.taxonomy_batch(text_list);
Console.WriteLine(taxonomy_batch);

```

```r
# for single sentence

url="https://apis.paralleldots.com/v4/taxonomy"
text="Apple was founded by Steve Jobs."
result<-taxonomy(url,text,api_key)
print(result)

# for multiple sentence

url="https://apis.paralleldots.com/v4/taxonomy_batch"
text='["Apple was founded by Steve Jobs","Apple Inc. is an American multinational technology company headquartered in Cupertino."]'
result<-taxonomy(url,text,api_key)
print(result)
```

> The above command returns JSON structured like this:

```json
{
    "taxonomy": [
        {
            "confidence_score": 0.9791216254,
            "tag": "TECH"
        },
        {
            "confidence_score": 0.0061760787,
            "tag": "BUSINESS"
        },
        {
            "confidence_score": 0.0059295441,
            "tag": "POLITICS"
        }
    ]
}

Batch Output -

{
    "taxonomy": [
        [
            {
                "confidence_score": 0.9791217446,
                "tag": "TECH"
            },
            {
                "confidence_score": 0.0061760736,
                "tag": "BUSINESS"
            },
            {
                "confidence_score": 0.0059295334,
                "tag": "POLITICS"
            }
        ],
        [
            {
                "confidence_score": 0.8196634054,
                "tag": "TECH"
            },
            {
                "confidence_score": 0.0500327237,
                "tag": "ENTERTAINMENT"
            },
            {
                "confidence_score": 0.0386201888,
                "tag": "TASTE"
            }
        ]
    ]
}

```

### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/taxonomy

`***POST*** /taxonomy` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text | query | Pass a long statement/multiple statement in case of batch | Yes | string/array |
| api_key | query | Apikey | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| taxonomy | Contains all the tags and their corresponding score | array | 
| tag | Name of the category | string |
| score | The confidence score of the tag in the text. It lies between 0 to 1 . Higher score states the higher confidence score of the output.| float |

**HTTP Error Codes**

| Code | Text | Description |
| ---- | ---- | ----------- |
| 200 |OK| Successful response |
| 304 |Not Modified| There was no new text to return. |
| 500 |Internal Server Error| Backend Error. |
| 400 |Bad Request| Please provide valid input parameter. |
| 401 |Unauthorized| Invalid Credentials. Please provide valid API key |
| 403 |Forbidden| Daily/Monthy Limit Exceeded. Please upgrade your account from your user dashboard at <a href="https://user.apis.paralleldots.com/user_dashboard">https://user.apis.paralleldots.com/user_dashboard</a>  |
| 429 |Too Many Requests| Too Many Requests. Please try after sometime. |
| 406 |Not Acceptable| Invalid Format. Parameter text should be string |

# /KEYWORDS
## ***POST*** 

**Summary:** Extract keywords from a block of text along with their confidence score

**Description:** Keywords Extractor API accepts two parameters - text and api_key and returns a json containing an array of keywords appearing in the input text along with their confidence score. 

```ruby
require 'paralleldots'

set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

# for single sentences
text="For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox."
puts(keywords(text))


# for multiple sentence as  array

text_array = ["For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.","U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports.."]

puts(batch_keywords(text_array))


```

```python
import paralleldots
paralleldots.set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")
# for single sentence
text="For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox."
response=paralleldots.keywords(text)
print(response)


# for multiple sentence as  array
text=["For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.","U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports."]
response=paralleldots.batch_keywords(text)
print(response) 


```

```shell
# for single sentence

curl -X POST -F 'text=For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/keywords

# for multiple sentence as  array

curl -X POST -F 'text=["For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.","U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports."]' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/keywords_batch
```

```java
import com.paralleldots.paralleldots.App;
import org.json.simple.JSONObject;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;
App pd = new App("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

// for single sentences
    String keywords = pd.keywords("For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox");
    System.out.println(keywords);

    
  
// for multiple sentence as array
   JSONArray text_list = (JSONArray)parser.parse("[ \"For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series.\", \"U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports.\" ]");

    String keywords_batch = pd.keywords_batch(text_list);
    System.out.println(keywords_batch);

    
  



```

```php
<?php
require(__DIR__ . '/vendor/paralleldots/apis/autoload.php');
set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

// for single sentence

echo keywords("For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.");

// for multiple sentence

$text_list = "[\"For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox\",\"U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports.\"]";
echo keywords_batch($text_list);

```

```csharp
using ParallelDots

// Initialize instance of api class
paralleldots pd = new paralleldots("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

// for single sentences
String keywords = pd.keywords("For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.");
Console.WriteLine(keywords);




// for multiple sentence
JArray text_list = JArray.Parse("[\"For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.\",  \"U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports.\"]");
String keywords_batch = pd.keywords_batch(text_list);
Console.WriteLine(keywords_batch);
```
```r

# for single sentence

url="https://apis.paralleldots.com/v4/keywords"
text="For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox."
result<-keywords(url,text,api_key)
print(result)

# for multiple sentence

url="https://apis.paralleldots.com/v4/keywords_batch"
text='["For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.","U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports."]'
result<-keywords(url,text,api_key)
print(result)

```

> The above command returns JSON structured like this:

```json
{
    "keywords": [
        {
            "keyword": "Yankees",
            "confidence_score": 0.778966
        },
        {
            "keyword": "comeback",
            "confidence_score": 0.877111
        },
        {
            "keyword": "Indians",
            "confidence_score": 0.990794
        },
        {
            "keyword": "American League Division Series",
            "confidence_score": 0.975588
        },
        {
            "keyword": "Astros",
            "confidence_score": 0.923083
        },
        {
            "keyword": "Chris Sale",
            "confidence_score": 0.935689
        },
        {
            "keyword": "Red Sox",
            "confidence_score": 0.959134
        }
    ]
}

Batch Output -

{
    "keywords": [
        [
            {
                "keyword": "Yankees",
                "confidence_score": 0.778966
            },
            {
                "keyword": "comeback",
                "confidence_score": 0.877111
            },
            {
                "keyword": "Indians",
                "confidence_score": 0.990794
            },
            {
                "keyword": "American League Division Series",
                "confidence_score": 0.975588
            },
            {
                "keyword": "Astros",
                "confidence_score": 0.923083
            },
            {
                "keyword": "Chris Sale",
                "confidence_score": 0.935689
            },
            {
                "keyword": "Red Sox",
                "confidence_score": 0.959134
            }
        ],
        [
            {
                "keyword": "stocks",
                "confidence_score": 0.82856
            },
            {
                "keyword": "higher",
                "confidence_score": 0.681598
            },
            {
                "keyword": "Friday",
                "confidence_score": 0.936368
            },
            {
                "keyword": "fivemonth high",
                "confidence_score": 0.853777
            },
            {
                "keyword": "gains",
                "confidence_score": 0.832542
            },
            {
                "keyword": "industrials",
                "confidence_score": 0.918522
            }
        ]
    ]
}

```

### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/keywords

`***POST*** /keywords` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text | query | Pass a long statement/multiple statement in case of batch | Yes | string/array |
| api_key | query | Apikey | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| keywords | Contains all the keywords and their corresponding score | array | 
| keyword | Name of the keyword | string |
| confidence_score | The confidence score of the keyword in the text. It lies between 0 to 1 . Higher score states the higher confidence score of the output.| float |

**HTTP Error Codes**

| Code | Text | Description |
| ---- | ---- | ----------- |
| 200 |OK| Successful response |
| 304 |Not Modified| There was no new text to return. |
| 500 |Internal Server Error| Backend Error. |
| 400 |Bad Request| Please provide valid input parameter. |
| 401 |Unauthorized| Invalid Credentials. Please provide valid API key |
| 403 |Forbidden| Daily/Monthy Limit Exceeded. Please upgrade your account from your user dashboard at <a href="https://user.apis.paralleldots.com/user_dashboard">https://user.apis.paralleldots.com/user_dashboard</a>  |
| 429 |Too Many Requests| Too Many Requests. Please try after sometime. |
| 406 |Not Acceptable| Invalid Format. Parameter text should be string |

# /EMOTION
## ***POST*** 

**Summary:** Find the emotion in a block of text

**Description:** Similar to sentiment API, Emotion API accepts text and api_key and returns a json response containing the overall emotion of the input text and confidence score for each of the emotion label (Happy, Sad, Angry, Excited, Sarcasm or Fear.). There are no limitation to the number of characters that you can pass to the Emotion API but for optimum results, please pass short texts (tweets, comments, news headlines, etc.)

```ruby
require 'paralleldots'

set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

# for single sentence
text= "I am trying to imagine you with a personality."
response=emotion(text, lang_code= "en")
puts(response) 



# for multiple sentence as array

text_array = ["I am trying to imagine you with a personality.","This is shit."]
puts(batch_emotion(text_array))



```

```python
import paralleldots
paralleldots.set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")
# for single sentence
text="I am trying to imagine you with a personality."
response=paralleldots.emotion(text)
print(response)



# for multiple sentence as array
text=["I am trying to imagine you with a personality.","This is shit."]
response=paralleldots.batch_emotion(text)
print(response)


```

```shell
<!-- # for single sentence -->
curl -X POST -F 'text=I am trying to imagine you with a personality.' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/emotion

<!-- # for multiple sentence as array -->
curl -X POST -F 'text=["I am trying to imagine you with a personality.","This is shit."]' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/emotion_batch
```

```java
import com.paralleldots.paralleldots.App;
import org.json.simple.JSONObject;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;
App pd = new App("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

// for single sentences
    
    String emotion = pd.emotion("I am trying to imagine you with a personality");
    System.out.println(emotion);

    
// for multiple sentence as array
    JSONArray text_list = (JSONArray)parser.parse("[ \"I am trying to imagine you with a personality\",  \"This is shit\"]");

    String emotion_batch = pd.emotion_batch(text_list);
    System.out.println(emotion_batch);
  

```

```php
<?php
require(__DIR__ . '/vendor/paralleldots/apis/autoload.php');
set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"); 
# for single sentence
echo emotion("I am trying to imagine you with a personality");

# for multiple sentence as array

$text_list = "[\"I am trying to imagine you with a personality\",\"This is shit\"]";
echo emotion_batch($text_list);

?>
```

```csharp
using ParallelDots

// Initialize instance of api class
paralleldots pd = new paralleldots("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

// for single sentence
String emotion = pd.emotion("I am trying to imagine you with a personality.");
Console.WriteLine(emotion);


// for multiple sentence as array
JArray text_list = JArray.Parse("[\"I am trying to imagine you with a personality.\", \"This is shit.\"]");

String emotion_batch = pd.emotion_batch(text_list);
Console.WriteLine(emotion_batch);


```

```r
# for single sentence

url="https://apis.paralleldots.com/v4/emotion"
text="I am trying to imagine you with a personality"
lang_code="en"
result<-emotion(url,text,api_key,lang_code)
print(result)

# for multiple sentence

url="https://apis.paralleldots.com/v4/emotion_batch"
text='["I am trying to imagine you with a personality","This is shit"]'
lang_code="en"
result<-emotion(url,text,api_key,lang_code)
print(result)

```

> The above command returns JSON structured like this:

```json
{
    "emotion": {
        "Bored": 0.0293023574,
        "Angry": 0.1041797904,
        "Sad": 0.0535987926,
        "Fear": 0.1313191025,
        "Happy": 0.3699369564,
        "Excited": 0.3116630007
    }
}

Batch Output -
 
{
    "emotion": [
        {
            "Bored": 0.0768371562,
            "Angry": 0.2231197248,
            "Sad": 0.2348101367,
            "Fear": 0.2431143526,
            "Happy": 0.1176188243,
            "Excited": 0.1044998055
        },
        {
            "Bored": 0.1220240678,
            "Angry": 0.4097742549,
            "Sad": 0.3024230883,
            "Fear": 0.1383221974,
            "Happy": 0.0160412186,
            "Excited": 0.011415173
        }
    ]
}

```

### HTTP Request

**Endpoint** https://apis.paralleldots.com/v4/emotion

`***POST*** /emotion` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text | formtext | Pass a statement/multiple statement in case of batch | Yes | string/array |
| api_key | formtext | Apikey | Yes | string |
| lang_code | formtext | Language Code | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| emotion | Type of emotion present in text i.e (angry,indifferent,sad,excited,happy) | object |
| probabilities | The confidence score of each of the emotion. It lies between 0 to 1 . Higher score states the higher confidence score of the output.| float |

**HTTP Error Codes**

| Code | Text | Description |
| ---- | ---- | ----------- |
| 200 |OK| Successful response |
| 304 |Not Modified| There was no new text to return. |
| 500 |Internal Server Error| Backend Error. |
| 400 |Bad Request| Please provide valid input parameter. |
| 401 |Unauthorized| Invalid Credentials. Please provide valid API key |
| 403 |Forbidden| Daily/Monthy Limit Exceeded. Please upgrade your account from your user dashboard at <a href="https://user.apis.paralleldots.com/user_dashboard">https://user.apis.paralleldots.com/user_dashboard</a>  |
| 429 |Too Many Requests| Too Many Requests. Please try after sometime. |
| 406 |Not Acceptable| Invalid Format. Parameter text should be string |

# /SARCASM
## ***POST*** 

**Summary:** Find the sarcasm in a block of text

**Description:** Sarcasm API accepts text and api_key and returns a json response containing the overall sarcasm of the input text. There are no limitation to the number of characters that you can pass to the Sarcasm API but for optimum results, please pass short texts (tweets, comments, news headlines, etc.)

```ruby
require 'paralleldots'

set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

# for single sentence
text= "I am trying to imagine you with a personality."
response=sarcasm(text, lang_code= "en")
puts(response) 



# for multiple sentence as array

text_array = ["I am trying to imagine you with a personality.","This is shit."]
puts(batch_sarcasm(text_array))



```

```python
import paralleldots
paralleldots.set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")
# for single sentence
text="I am trying to imagine you with a personality."
response=paralleldots.sarcasm(text)
print(response)



# for multiple sentence as array
text=["I am trying to imagine you with a personality.","This is shit."]
response=paralleldots.batch_sarcasm(text)
print(response)


```

```shell
<!-- # for single sentence -->
curl -X POST -F 'text=I am trying to imagine you with a personality.' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/sarcasm

<!-- # for multiple sentence as array -->
curl -X POST -F 'text=["I am trying to imagine you with a personality.","This is shit."]' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/sarcasm_batch
```

```java
import com.paralleldots.paralleldots.App;
import org.json.simple.JSONObject;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;
App pd = new App("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

// for single sentences
    
    String sarcasm = pd.sarcasm("I am trying to imagine you with a personality");
    System.out.println(sarcasm);

    
// for multiple sentence as array
    JSONArray text_list = (JSONArray)parser.parse("[ \"I am trying to imagine you with a personality\",  \"This is shit\"]");

    String sarcasm_batch = pd.sarcasm_batch(text_list);
    System.out.println(sarcasm_batch);
  

```

```php
<?php
require(__DIR__ . '/vendor/paralleldots/apis/autoload.php');
set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"); 
# for single sentence
echo sarcasm("I am trying to imagine you with a personality");

# for multiple sentence as array

$text_list = "[\"I am trying to imagine you with a personality\",\"This is shit\"]";
echo sarcasm_batch($text_list);

?>
```

```csharp
using ParallelDots

// Initialize instance of api class
paralleldots pd = new paralleldots("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

// for single sentence
String sarcasm = pd.sarcasm("I am trying to imagine you with a personality.");
Console.WriteLine(sarcasm);


// for multiple sentence as array
JArray text_list = JArray.Parse("[\"I am trying to imagine you with a personality.\", \"This is shit.\"]");

String sarcasm_batch = pd.sarcasm_batch(text_list);
Console.WriteLine(sarcasm_batch);


```

```r
# for single sentence

url="https://apis.paralleldots.com/v4/sarcasm"
text="I am trying to imagine you with a personality"
lang_code="en"
result<-sarcasm(url,text,api_key,lang_code)
print(result)

# for multiple sentence

url="https://apis.paralleldots.com/v4/sarcasm_batch"
text='["I am trying to imagine you with a personality","This is shit"]'
lang_code="en"
result<-sarcasm(url,text,api_key,lang_code)
print(result)

```

> The above command returns JSON structured like this:

```json
{
    "Sarcastic": 0.5877064532,
    "Non-Sarcastic": 0.4122935468
}

Batch Output -
[
    {
        "Sarcastic": 0.6234579586,
        "Non-Sarcastic": 0.3765420414
    },
    {
        "Sarcastic": 0.6223731263,
        "Non-Sarcastic": 0.3776268737
    }
]

```

### HTTP Request

**Endpoint** https://apis.paralleldots.com/v4/sarcasm

`***POST*** /sarcasm` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text | formtext | Pass a statement/multiple statement in case of batch | Yes | string/array |
| api_key | formtext | Apikey | Yes | string |
| lang_code | formtext | Language Code | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| emotion | Type of sarcasm present in text | object |
| probabilities | The confidence score of each of the sarcasm. It lies between 0 to 1 . Higher score states the higher confidence score of the output.| float |

**HTTP Error Codes**

| Code | Text | Description |
| ---- | ---- | ----------- |
| 200 |OK| Successful response |
| 304 |Not Modified| There was no new text to return. |
| 500 |Internal Server Error| Backend Error. |
| 400 |Bad Request| Please provide valid input parameter. |
| 401 |Unauthorized| Invalid Credentials. Please provide valid API key |
| 403 |Forbidden| Daily/Monthy Limit Exceeded. Please upgrade your account from your user dashboard at <a href="https://user.apis.paralleldots.com/user_dashboard">https://user.apis.paralleldots.com/user_dashboard</a>  |
| 429 |Too Many Requests| Too Many Requests. Please try after sometime. |
| 406 |Not Acceptable| Invalid Format. Parameter text should be string |

# /INTENT
## ***POST*** 

**Summary:** Find intent of the user input

**Description:** Intent API classifies the intent of a block of text as one of opinion, news, marketing, complaint, suggestion, apprectiation, query. The API accepts accepts text and api_key and returns a json response containing the overall intent of the input text and confidence score for each of the intent label. Use this API to filter our spam or marketing tweets to identify genuine tweets, building a conversational bot to understand user's intent or monitor complaints in real-time on social media channels or your own feedback platform.

```ruby
require 'paralleldots'

set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")


# for single sentence
text="How do I cancel my ticket from the app?"
puts(intent(text))




# for multiple sentence

text_array = ["How do I cancel my ticket from the app?","20% off on your next Uber ride"]
puts(batch_intent(text_array))



```

```python
import paralleldots
paralleldots.set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")
# for single sentence
text="How do I cancel my ticket from the app?"
response=paralleldots.intent(text)
print(response)

# for multiple sentence as array
text=["How do I cancel my ticket from the app?","20% off on your next Uber ride"]
response=paralleldots.batch_intent(text)
print(response)


```

```shell
# for single sentence

curl -X POST -F 'text=How do I cancel my ticket from the app?' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/intent

# for multiple sentence as array

curl -X POST -F 'text=["How do I cancel my ticket from the app?","20% off on your next Uber ride"]' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/intent_batch

```

```java
import com.paralleldots.paralleldots.App;
import org.json.simple.JSONObject;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;
App pd = new App("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");
// for single sentences
   String intent = pd.intent("How do I cancel my ticket from the app");
   System.out.println(intent);
 
// for multiple sentence as array
    JSONArray text_list = (JSONArray)parser.parse("[\"How do I cancel my ticket from the app\",\"20%off on your next Uber ride\"]");
    String intent_batch = pd.intent_batch(text_list);
    System.out.println(intent_batch); 
```

```php
<?php
require(__DIR__ . '/vendor/paralleldots/apis/autoload.php');
set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");
# for single sentence 

echo intent("How do I cancel my ticket from the app");

# for multiple sentence as array

$text_list = "[\"How do I cancel my ticket from the app?\",\"20% off on your next Uber ride\"]";
echo intent_batch($text_list)

```

```csharp
using ParallelDots

// Initialize instance of api class
paralleldots pd = new paralleldots("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

// for single sentence

String intent = pd.intent("How do I cancel my ticket from the app?");
Console.WriteLine(intent);



// for multiple sentence as array

JArray text_list = JArray.Parse("[\"How do I cancel my ticket from the app?\", \"20% off on your next Uber ride?\"]");
String intent_batch = pd.intent_batch(text_list);
Console.WriteLine(intent_batch);



```

```r
# for single sentence

url="https://apis.paralleldots.com/v4/intent"
text="How do I cancel my ticket from the app?"
result<-intent(url,text,api_key)
print(result)

# for multiple sentence

url="https://apis.paralleldots.com/v4/intent_batch"
text='["How do I cancel my ticket from the app?","20% off on your next Uber ride"]'
result<-intent(url,text,api_key)
print(result)

```


> The above command returns JSON structured like this:

```json
{
    "intent": {
        "news": 0,
        "query": 0.999,
        "spam": 0.001,
        "marketing": 0,
        "feedback": 0.001
    }
}

Batch Output -
 
{
    "intent": [
        {
            "intent": {
                "news": 0,
                "query": 0.999,
                "spam": 0.001,
                "marketing": 0,
                "feedback": 0.001
            }
        },
        {
            "intent": {
                "news": 0.026,
                "query": 0.001,
                "spam": 0.39,
                "marketing": 0.496,
                "feedback": 0.087
            }
        }
    ]
}

```

### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/intent

`***POST*** /intent` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text | formtext | Pass a statement/multiple statement in case of batch | Yes | string/array |
| api_key | formtext | Apikey | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| intent | Type of intent present in text i.e (marketing,news,query,feedback/opinion,spam/junk) | object |
| probabilities | The confidence score of each of the intent. It lies between 0 to 1 . Higher score states the higher confidence score of the output.| float |

**HTTP Error Codes**

| Code | Text | Description |
| ---- | ---- | ----------- |
| 200 |OK| Successful response |
| 304 |Not Modified| There was no new text to return. |
| 500 |Internal Server Error| Backend Error. |
| 400 |Bad Request| Please provide valid input parameter. |
| 401 |Unauthorized| Invalid Credentials. Please provide valid API key |
| 403 |Forbidden| Daily/Monthy Limit Exceeded. Please upgrade your account from your user dashboard at <a href="https://user.apis.paralleldots.com/user_dashboard">https://user.apis.paralleldots.com/user_dashboard</a>  |
| 429 |Too Many Requests| Too Many Requests. Please try after sometime. |
| 406 |Not Acceptable| Invalid Format. Parameter text should be string |

# /ABUSE
## ***POST*** 

**Summary:** Filter abusive content from a text corpus

**Description:** Abusive content specifier specifies whether the content is abusive or not. The API accepts two parameters - text and api_key and returns a json response classifying whether the input text has abusive content.

```ruby
require 'paralleldots'

set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

# for single sentence
text="you f**king a$$hole"
puts(abuse( text ))


# for multiple sentences

text_array = ["you f**king a$$hole","fuck this shit"]
puts(batch_abuse( text_array ))


```

```python
import paralleldots
paralleldots.set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")
# for single sentence
text="you f**king a$$hole"
response=paralleldots.abuse(text)
print(response)



# for multiple sentence as array
text=["you f**king a$$hole","fuck this shit"]
response=paralleldots.batch_abuse(text)
print(response)


```

```shell
 # for single sentence

curl -X POST -F 'text=you f**king a$$hole' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/abuse

# for multiple sentence as array

curl -X POST -F 'text=["you f**king a$$hole","fuck this shit"]' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/abuse_batch

```

```java
import com.paralleldots.paralleldots.App;
import org.json.simple.JSONObject;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;
App pd = new App("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");
// for single sentences
   String abuse = pd.abuse("you f**king a$$hole");
   System.out.println(abuse);

    


// for multiple sentence as array
    JSONArray text_list = (JSONArray)parser.parse("[\"you f**king ass hole\",\"fuck this shit\"]");
    String abuse_batch = pd.abuse_batch(text_list);
    System.out.println(abuse_batch);

```

```php
<?php
require(__DIR__ . '/vendor/paralleldots/apis/autoload.php');
set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");
# for single sentence

echo abuse("you f**king ass hole");


# for multiple sentence as array

$text_list = "[\"you f**king ass hole\",\"fuck this shit\"]";
echo abuse_batch($text_list);
?>

```

```csharp
using ParallelDots

// Initialize instance of api class
paralleldots pd = new paralleldots("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

// for single sentence

String abuse = pd.abuse("you f**king a$$hole");
Console.WriteLine(abuse);



// for multiple sentence as array

JArray text_list = JArray.Parse("[\"you f**king a$$hole.\",  \"fuck this shit.\"]");


String abuse_batch = pd.abuse_batch(text_list);
Console.WriteLine(abuse_batch);


```


```r

# for single sentence

url="https://apis.paralleldots.com/v4/abuse"
text="you f**king a$$hole"
result<-abuse(url,text,api_key)
print(result)

# for multiple sentence 

url="https://apis.paralleldots.com/v4/abuse_batch"
text='["You f***ing ass hole","f**k this shit"]'
result<-abuse(url,text,api_key)
print(result)
```
> The above command returns JSON structured like this:

```json
  [
    {
    "abusive": 0.0236050598,
    "hate_speech": 0.9761587977,
    "neither": 0.0002360792
    }
]
Batch Output -
 
 {
    "abuse": [
        [
            {
            "abusive": 0.0236050598,
            "hate_speech": 0.9761587977,
            "neither": 0.0002360792
            }
        ],
        [
            {
            "abusive": 0.9942116141,
            "hate_speech": 0.0056449119,
            "neither": 0.000143452
            }  
        ]
    ]
}
```

### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/abuse

`***POST*** /abuse` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text | formtext | Pass a statement/multiple statement in case of batch | Yes | string/array |
| api_key | formtext | Apikey | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| Abuse or Non-Abuse | Nature of the text | object |
| confidence_score | The confidence score of the sentence_type. It lies between 0 to 1 . Higher score states the higher confidence score of the output.| float |

**HTTP Error Codes**

| Code | Text | Description |
| ---- | ---- | ----------- |
| 200 |OK| Successful response |
| 304 |Not Modified| There was no new text to return. |
| 500 |Internal Server Error| Backend Error. |
| 400 |Bad Request| Please provide valid input parameter. |
| 401 |Unauthorized| Invalid Credentials. Please provide valid API key |
| 403 |Forbidden| Daily/Monthy Limit Exceeded. Please upgrade your account from your user dashboard at <a href="https://user.apis.paralleldots.com/user_dashboard">https://user.apis.paralleldots.com/user_dashboard</a>  |
| 429 |Too Many Requests| Too Many Requests. Please try after sometime. |
| 406 |Not Acceptable| Invalid Format. Parameter text should be string |

# /CUSTOM_CLASSIFIER
## ***POST*** 

**Summary:** Custom Classifier API classifies an input text into user's custom defined categories

**Description:** Custom Classifier eliminates the need to prepare a tranining text for building your own text classification model. The API accepts three parameters - text, category and api_key. Category list is a key-value pair object which contains main-category as the key and an array containing sub-categories as the corresponding value. The API returns a json response with the category list sorted in the descending order of confidence score. 

**Please note that only the main categories will be classified in the response, sub-categories serve to expand the domain of the classification model to improve the classification accuracy. The classifier does not categorize the input text into sub-categories.**

**Note:**Sub-categories are optional, pass an empty array ([]) if you do not want to specify sub-categories.

```ruby
require 'paralleldots'

set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

category  = { "finance": [ "markets", "economy", "shares" ], "world politics": [ "diplomacy", "UN", "war" ] }
text="Donald Trump is the President of the United States of America."
puts( custom_classifier( text, category ) )


```

```python
import paralleldots
paralleldots.set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")
category  ={ "finance": [ "markets", "economy", "shares" ], "world politics": [ "diplomacy", "UN", "war" ] }
text="Donald Trump is the President of the United States of America."
response=paralleldots.custom_classifier(text,category)
print(response)

```

```shell
curl --request POST   --url https://apis.paralleldots.com/v4/custom_classifier   --header 'Cache-Control: no-cache' \   --header 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'   --form 'text=Donald Trump is the President of the United States of America.'   --form 'category={ "finance": [ "markets", "economy", "shares" ], "world politics": [ "diplomacy", "UN", "war" ] }'   --form api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

```java


import com.paralleldots.paralleldots.App;
import org.json.simple.JSONObject;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;

App pd = new App("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");
JSONParser parser = new JSONParser();
JSONObject category = (JSONObject)parser.parse("{\"world politics\": [\"diplomacy\", \"UN\", \"war\"], \"finance\": [\"markets\", \"economy\", \"shares\"]}".trim());

String custom_classifier = pd.custom_classifier("Donald Trump is the President of the United States of America.&category", category);
System.out.println(custom_classifier);
 
```

```php
<?php
require(__DIR__ . '/vendor/paralleldots/apis/autoload.php');
set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"); 

$obj = "{\"world politics\":[\"diplomacy\",\"UN\",\"war\"],\"finance\":[\"markets\",\"economy\",\"shares\"]}";
echo custom_classifier("Donald Trump is the President of the United States of America.", $obj);

?>

```

```csharp
using ParallelDots

// Initialize instance of api class
paralleldots pd = new paralleldots("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

JObject category = JObject.Parse(@"{ "finance": [ "markets", "economy", "shares" ], "world politics": [ "diplomacy", "UN", "war" ] }");

String custom_classifier = pd.custom_classifier("Donald Trump is the President of the United States of America", category);
Console.WriteLine(custom_classifier);


```

```r
url="https://apis.paralleldots.com/v4/custom_classifier"
text="Donald Trump is the President of the United States of America"
category='{ "finance": [ "markets", "economy", "shares" ], "world politics": [ "diplomacy", "UN", "war" ] }'
result<-custom_classifier(url,text,api_key,category)
print(result)
```

> The above command returns JSON structured like this:

```json
{
    "taxonomy": [
        {
            "tag": "world politics",
            "confidence_score": 0.9589139819
        },
        {
            "tag": "finance",
            "confidence_score": 0.4599229991
        }
    ]
}

```

### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/custom_classifier

`***POST*** /custom_classifier`

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text | query | Pass a statement | Yes | string |
| api_key | query | Apikey | Yes | string |
| category | query | It is dictionary of lists where key is the category name and list values are sub-categories. | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| taxonomy | Contains all the tags and their corresponding score | array | 
| tag | Name of the category | string |
| score | The confidence score of the tag in the text. It lies between 0 to 1 . Higher score states the higher confidence score of the output.| float |

**HTTP Error Codes**

| Code | Text | Description |
| ---- | ---- | ----------- |
| 200 |OK| Successful response |
| 304 |Not Modified| There was no new text to return. |
| 500 |Internal Server Error| Backend Error. |
| 400 |Bad Request| Please provide valid input parameter. |
| 401 |Unauthorized| Invalid Credentials. Please provide valid API key |
| 403 |Forbidden| Daily/Monthy Limit Exceeded. Please upgrade your account from your user dashboard at <a href="https://user.apis.paralleldots.com/user_dashboard">https://user.apis.paralleldots.com/user_dashboard</a>  |
| 429 |Too Many Requests| Too Many Requests. Please try after sometime. |
| 406 |Not Acceptable| Invalid Format. Parameter text should be string |


# /PHRASE_EXTRACTOR
## ***POST*** 

**Summary:** Phrase Extractor find key phrases in a block of text.

**Description:** Phrase Extractor API accepts two parameters - text and api_key and returns a json containing an array of phrases appearing in the input text along with their confidence score.


```ruby
require 'paralleldots'

set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

# for single sentence
text="For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.."
puts( phrase_extractor( text ) )



# for multiple sentence as array

text_array = ["For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox..","U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports."]

puts(batch_phrase_extractor( text_array ))


```

```python
import paralleldots
paralleldots.set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

# for single sentence
text="For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.."
response=paralleldots.phrase_extractor(text)
print(response)



# for multiple sentence as array
text=["For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox..","U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports."]
response=paralleldots.batch_phrase_extractor(text)
print(response) 



```

```shell
# for single sentence

curl -X POST -F 'text=For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/phrase_extractor

# for multiple sentence as array

curl -X POST -F 'text=["For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox..","U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports."]' -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' https://apis.paralleldots.com/v4/phrase_extractor_batch
```

```java
import com.paralleldots.paralleldots.App;
import org.json.simple.JSONObject;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;
App pd = new App("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");
// for single sentences

    String phrase_extractor = pd.phrase_extractor("For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox");
    System.out.println(phrase_extractor);
    
    
  
// for multiple sentence as array
   JSONArray text_list = (JSONArray)parser.parse("[\"For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox\",\"U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports.\"]");
   String phrase_extractor_batch = pd.phrase_extractor_batch(text_list);
   System.out.println(phrase_extractor_batch);



    
  

```

```php
<?php
require(__DIR__ . '/vendor/paralleldots/apis/autoload.php');
set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

# for single sentence

echo phrase_extractor("For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.");




# for multiple sentence as array


$text_list = "[\"For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.\",\"U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports.\"]";
echo phrase_extractor_batch($text_list);




?>
```

```csharp
using ParallelDots

// Initialize instance of api class
paralleldots pd = new paralleldots("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

// for single sentence 
Console.WriteLine(phrase_extractor);


// for multiple sentence as array

JObject text_array = JObject.Parse(@'["For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.","U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports."]');
String phrase_extractor_batch = pd.phrase_extractor_batch(text_array);
Console.WriteLine(phrase_extractor_batch);



```
 
```r

# for single sentence

url="https://apis.paralleldots.com/v4/phrase_extractor"
text="For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox."
result<-phrase_extractor(url,text,api_key)
print(result)

# for multiple sentence

url="https://apis.paralleldots.com/v4/phrase_extractor_batch"
text='["For the Yankees, it took a stunning comeback after being down 2-0 to the Indians in the American League Division Series. For the Astros, it took beating Chris Sale to top the Red Sox.","U.S. stocks edged higher on Friday, with the S&P 500 hitting a more than five-month high, as gains in industrials and other areas offset a drop in financials. Fred Katayama reports."]'
result<-phrase_extractor(url,text,api_key)
print(result)
```
> The above command returns JSON structured like this:

```json
{
    "keywords": [
        {
            "keyword": "Red Sox",
            "relevance_score": 2
        },
        {
            "keyword": "stunning comeback",
            "relevance_score": 2
        },
        {
            "keyword": "Yankees",
            "relevance_score": 1
        },
        {
            "keyword": "Astros",
            "relevance_score": 1
        },
        {
            "keyword": "Indians",
            "relevance_score": 1
        },
        {
            "keyword": "American League Division Series",
            "relevance_score": 4
        },
        {
            "keyword": "Chris Sale",
            "relevance_score": 2
        }
    ]
}

Batch Output -

{
    "phrases": [
        [
            {
                "keyword": "Red Sox",
                "relevance_score": 2
            },
            {
                "keyword": "stunning comeback",
                "relevance_score": 2
            },
            {
                "keyword": "Yankees",
                "relevance_score": 1
            },
            {
                "keyword": "Astros",
                "relevance_score": 1
            },
            {
                "keyword": "Indians",
                "relevance_score": 1
            },
            {
                "keyword": "American League Division Series",
                "relevance_score": 4
            },
            {
                "keyword": "Chris Sale",
                "relevance_score": 2
            }
        ],
        [
            {
                "keyword": "U.S. stocks",
                "relevance_score": 2
            },
            {
                "keyword": "month high",
                "relevance_score": 2
            },
            {
                "keyword": "other areas",
                "relevance_score": 2
            },
            {
                "keyword": "Friday",
                "relevance_score": 1
            },
            {
                "keyword": "S&P",
                "relevance_score": 1
            },
            {
                "keyword": "Fred Katayama",
                "relevance_score": 2
            }
        ]
    ]
}
```

### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/phrase_extractor

`***POST*** /phrase_extractor` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text | query | Pass a statement/multiple statement in case of batch | Yes | string/array |
| api_key | query | Apikey | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| keywords | Contains all the keywords and their corresponding score | array | 
| keyword | Name of the keyword | string |
| relevance_score | The confidence score of the keyword in the text. It lies between 1 to length of the sentence . Higher score states the higher confidence score of the output.| float |

**HTTP Error Codes**

| Code | Text | Description |
| ---- | ---- | ----------- |
| 200 |OK| Successful response |
| 304 |Not Modified| There was no new text to return. |
| 500 |Internal Server Error| Backend Error. |
| 400 |Bad Request| Please provide valid input parameter. |
| 401 |Unauthorized| Invalid Credentials. Please provide valid API key |
| 403 |Forbidden| Daily/Monthy Limit Exceeded. Please upgrade your account from your user dashboard at <a href="https://user.apis.paralleldots.com/user_dashboard">https://user.apis.paralleldots.com/user_dashboard</a>  |
| 429 |Too Many Requests| Too Many Requests. Please try after sometime. |
| 406 |Not Acceptable| Invalid Format. Parameter text should be string |

# /MULTILANG KEYWORDS
## ***POST*** 

**Summary:** Multilang Keywords finds keywords in all the supported languages mentioned above except Chinese.

**Description:** Multilang Keywords Extractor API accepts three parameters - text, lang_code and api_key and returns a json containing an array of keywords appearing in the input text along with their confidence score.
The API defaults English language if no lang_code is specified.


```ruby
require 'paralleldots'

set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

lang_code="fr"
lang_text="C'est un environnement très hostile, si vous choisissez de débattre ici, vous serez vicieusement attaqué par l'opposition."
puts( multilang_keywords( lang_text, lang_code ) )


```

```python
import paralleldots
paralleldots.set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx")

text= "C'est un environnement très hostile, si vous choisissez de débattre ici, vous serez vicieusement attaqué par l'opposition."
lang_code="fr"
response=paralleldots.multilang_keywords(text,lang_code)
print(response)

```

```shell
curl -X POST -F "text=C'est un environnement très hostile, si vous choisissez de débattre ici, vous serez vicieusement attaqué par l'opposition." -F 'api_key=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx' -F 'lang_code=fr' https://apis.paralleldots.com/v4/multilang_keywords
```

```java
import com.paralleldots.paralleldots.App;
import org.json.simple.JSONObject;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;
App pd = new App("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");
// for single sentences
    String multilang_keywords = pd.multilang_keywords("C'est un environnement très hostile, si vous choisissez de débattre ici, vous serez vicieusement attaqué par l'opposition.", "fr");
    System.out.println(multilang_keywords);

    
 
```

```php
<?php
require(__DIR__ . '/vendor/paralleldots/apis/autoload.php');
set_api_key("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"); 

echo multilang_keywords("C'est un environnement très hostile, si vous choisissez de débattre ici, vous serez vicieusement attaqué par l'opposition.", "fr");




?>

```

```csharp
using ParallelDots

// Initialize instance of api class
paralleldots pd = new paralleldots("xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx");

String multilang_keywords = pd.multilang_keywords("C'est un environnement très hostile, si vous choisissez de débattre ici, vous serez vicieusement attaqué par l'opposition", "fr");
Console.WriteLine(multilang_keywords);

```

```r
url="https://apis.paralleldots.com/v4/multilang_keywords"
text="C'est un environnement très hostile, si vous choisissez de débattre ici, vous serez vicieusement attaqué par l'opposition"
lang_code="fr"
result<-multilang_keywords(url,text,api_key,lang_code)
print(result)
```

> The above command returns JSON structured like this:

```json
{
    "keywords": [
        {
            "keyword": "vicieusement attaqué",
            "confidence_score": 4
        },
        {
            "keyword": "opposition",
            "confidence_score": 1
        },
        {
            "keyword": "hostile",
            "confidence_score": 1
        },
        {
            "keyword": "environnement",
            "confidence_score": 1
        },
        {
            "keyword": "débattre",
            "confidence_score": 1
        },
        {
            "keyword": "choisissez",
            "confidence_score": 1
        }
    ]
}

```

### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/multilang_keywords

`***POST*** /multilang_keywords` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text | query | Pass a statement | Yes | string |
| api_key | query | Apikey | Yes | string |
| lang_code | query | Language Code | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| keywords | Contains all the keywords | array |

**HTTP Error Codes**

| Code | Text | Description |
| ---- | ---- | ----------- |
| 200 |OK| Successful response |
| 304 |Not Modified| There was no new text to return. |
| 500 |Internal Server Error| Backend Error. |
| 400 |Bad Request| Please provide valid input parameter. |
| 401 |Unauthorized| Invalid Credentials. Please provide valid API key |
| 403 |Forbidden| Daily/Monthy Limit Exceeded. Please upgrade your account from your user dashboard at <a href="https://user.apis.paralleldots.com/user_dashboard">https://user.apis.paralleldots.com/user_dashboard</a>  |
| 429 |Too Many Requests| Too Many Requests. Please try after sometime. |
| 406 |Not Acceptable| Invalid Format. Parameter text should be string |

# SEMANTIC SIMILARITY 2.O

**Summary:** Semantic Text API finds similar documents corresponding to an input document 

**Description:** Sematic text API consists of five different phases as discussed below:

   - Adding a corpus of documents for indexing
   - Training a model to compute similarity
   - Predicting similar documents for a new document
   - Updating the similarity model with new documents
   - See all information related to model like number of documents trained and untrained.

Such an API can be used to build real-time chatbot applications to find responses to similar queries, automating FAQs and building semantic search engines for your documents that goes beyond traditional keyword search and bag of words approaches.

## **/add/data**
**POST**
 
**Description:** add_data API allows you to add documents to a new model or update an existing model. It accepts different parameters corresponding to one of the two operation codes - **new and update**. Operation code gives you control over which operation you want to perform. 

- New accepts three parameters- text, operation_code and api_key and returns a json containing the number of documents uploaded and a model id (please take a note of your model id). We recommend sending up to 100 documents at a time.

- Update accept four parameters - text, operation_code, api_key and model_id ( corresponding to the model you want to    update ) and return json data containing number of documents uploaded in that model.


```ruby
require 'rest-client'
require 'open-uri'
require 'json'
# for new(operation_code)
data=["Come on lets play together","Team performed well overall"]
response = RestClient.post "https://apis.paralleldots.com/v4/semantic/similarity/add/data", { api_key: "<api_key>", text:data.to_json ,operation_code:"new"}
response = JSON.parse( response )
puts response

# for update(operation_code)

response = RestClient.post "https://apis.paralleldots.com/v4/semantic/similarity/add/data", { api_key: "<api_key>", text:data.to_json ,operation_code:"update",model_id:"<model_id>"}
response = JSON.parse( response )
puts response

```

```python
import requests
import json

# for new(operation_code)
data=["Come on lets play together","Team performed well overall"]
response = requests.post("https://apis.paralleldots.com/v4/semantic/similarity/add/data", data={ "api_key": "<api_key>", "text":json.dumps(data) ,"operation_code":"new"})

# for update(operation_code)

response = requests.post("https://apis.paralleldots.com/v4/semantic/similarity/add/data", data={ "api_key": "<api_key>", "text":json.dumps(data) ,"operation_code":"update","model_id":"<model_id>"})

print(response.json())

```

```shell
# for new(operation_code)

curl -X POST -F 'text=["Come on lets play together","Team performed well overall"]' -F "operation_code=new" -F "api_key=<api_key>" https://apis.paralleldots.com/v4/semantic/similarity/add/data

# for update(operation_code)

curl -X POST -F 'text=["Come on lets play together","Team performed well overall"]' -F "operation_code=update" -F "api_key=<api_key>" -F "model_id=<model_id>" https://apis.paralleldots.com/v4/semantic/similarity/add/data
```

```java
import java.io.IOException;
import okhttp3.OkHttpClient;
import okhttp3.Request;
import okhttp3.Response;
import okhttp3.MediaType;
import okhttp3.MultipartBody;
import okhttp3.RequestBody;
import okhttp3.ResponseBody;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;
// for new(operation_code)

JSONParser parser = new JSONParser();  
JSONArray text_list = (JSONArray)parser.parse("[\"Come on, lets play together\",\"Team performed well overall\"]");
String api_key = "<api_key>"  ;
String operation_code = "new";

String url = "https://apis.paralleldots.com/v4/semantic/similarity/add/data";
    OkHttpClient client = new OkHttpClient();
            RequestBody requestBody = new MultipartBody.Builder()
            .setType(MultipartBody.FORM)
            .addFormDataPart("api_key", api_key)
            .addFormDataPart("text", text_list.toString())
            .addFormDataPart("operation_code", operation_code)
            .build();
            Request request = new Request.Builder()
              .url(url)
              .post(requestBody)
              .addHeader("cache-control", "no-cache")
              .build();       
Response response = client.newCall(request).execute();
System.out.println(response.body().string());

//  for update(operation_code)
String operation_code = "update";
String model_id = "<model_id>";
String url = "https://apis.paralleldots.com/v4/semantic/similarity/add/data";
    OkHttpClient client = new OkHttpClient();
            RequestBody requestBody = new MultipartBody.Builder()
            .setType(MultipartBody.FORM)
            .addFormDataPart("api_key", api_key)
            .addFormDataPart("text", text_list.toString())
            .addFormDataPart("operation_code", operation_code)
            .addFormDataPart("model_id", model_id)
            .build();
            Request request = new Request.Builder()
              .url(url)
              .post(requestBody)
              .addHeader("cache-control", "no-cache")
              .build();       
Response response = client.newCall(request).execute();
System.out.println(response.body().string());
 
```

```php
<?php
$curl = curl_init();

# for new(operation_code)

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://apis.paralleldots.com/v4/semantic/similarity/add/data",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"operation_code\"\r\n\r\nnew\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"text\"\r\n\r\n[\"Come on,lets play together\",\"Team performed well overall.\"]\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"api_key\"\r\n\r\n<api_key>\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
  CURLOPT_HTTPHEADER => array(
    "Cache-Control: no-cache",
    "content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW"
  ),
));

# for update(operation_code)

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://apis.paralleldots.com/v4/semantic/similarity/add/data",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"operation_code\"\r\n\r\nupdate\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"model_id\"\r\n\r\n<model_id>\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"text\"\r\n\r\n[\"Come on,lets play together\",\"Team performed well overall.\"]\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"api_key\"\r\n\r\n<api_key>\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
  CURLOPT_HTTPHEADER => array(
    "Cache-Control: no-cache",
    "content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}

```

```csharp
using System;
using Newtonsoft.Json.Linq;
using RestSharp;
using System.IO;
// for new(operation_code)

JObject text_array = JObject.Parse(@"[ 'Come on,lets play together','Team performed well overall.']");
var api_key="<api_key>";
var operation_code="new";
var url = "https://apis.paralleldots.com/v4/semantic/similarity/add/data";
var client = new RestClient(url);
var request = new RestRequest(Method.POST);
request.AddHeader("text", text_array);
request.AddHeader("operation_code", operation_code);
request.AddHeader("api_key", api_key);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("content-type", "application/json");
request.AddHeader("source", "c#wrapper");
IRestResponse response = client.Execute(request);
Console.WriteLine( response.Content.ToString());

//  for update(operation_code)

JObject text_array = JObject.Parse(@"[ 'Come on,lets play together','Team performed well overall.']");
var api_key="<api_key>";
var operation_code="update";
var model_id="<model_id>";
var url = "https://apis.paralleldots.com/v4/semantic/similarity/add/data";
var client = new RestClient(url);
var request = new RestRequest(Method.POST);
request.AddHeader("text", text_array);
request.AddHeader("model_id",model_id);
request.AddHeader("operation_code", operation_code);
request.AddHeader("api_key", api_key);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("content-type", "application/json");
request.AddHeader("source", "c#wrapper");
IRestResponse response = client.Execute(request);
Console.WriteLine( response.Content.ToString());
```

```r
library("httr")
library("jsonlite")

url="https://apis.paralleldots.com/v4/semantic/similarity/add/data"
data='["Come on lets play together","Team performed well overall"]'

# for new(operation_code)

operation_code="new"
api_key="<api_key>"

req <- POST(url,
              body = list(
                text = data,
                api_key=api_key,
                operation_code=operation_code
              ),
              encode = "multipart"
  )
stop_for_status(req)
result<-content(req)
print (toJSON(result, auto_unbox = TRUE))

# for update(operation_code)
data='["Come on lets play together","Team performed well overall"]'
model_id='<model_id>'
operation_code="update"
api_key="<api_key>"

req <- POST(url,
              body = list(
                text = data,
                api_key=api_key,
                model_id=model_id,
                operation_code=operation_code
              ),
              encode = "multipart"
  )
stop_for_status(req)
result<-content(req)
print (toJSON(result, auto_unbox = TRUE))

```

> The above command returns JSON structured like this:

```json

// for new(operation_code)

{
  "model_id": "xxxxxx",
  "number of document": 10,
  "code":200
}

// for update(operation_code)

{
    "update": "Succesfully",
    "number of document": 20,
    "code": 200
}
```
### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/semantic/similarity/add/data

`***POST*** /add/data` 

**Parameters**


**new(Operation Code)**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text | query | Pass a statement | Yes | array |
| api_key | query | API key | Yes | string |
| operation_code | query | new | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| model_id | a unique id to identify your model  | string |

**update(Operation Code)**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| text | query | Pass a statement | Yes | array  |
| api_key | query | API key | Yes | string |
| operation_code | query | update | Yes | string |
| model_id | query | a unique id to identify your model | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| documents update | message of opeartion | string |

## ***/train***
**POST**

**Discription:** train API allows to train an existing model. It accepts two parameters- model_id and api_key.

Addtitionally, Train API can accept an operation code - status. Operation code allows you to check the training status of model and will return complete or in progress depending upon whether your model is trained or is still training. 

```ruby
require 'rest-client'
require 'open-uri'
require 'json'
response = RestClient.post "https://apis.paralleldots.com/v4/semantic/similarity/train", { api_key: "<api_key>", model_id:"<model_id>"}
response = JSON.parse( response )
puts response

#for checking status of training

response = RestClient.post "https://apis.paralleldots.com/v4/semantic/similarity/train", { api_key: "<api_key>", model_id:"<model_id>", operation_code:"status"}
response = JSON.parse( response )
puts response


```

```python
import requests
import json


response = requests.post("https://apis.paralleldots.com/v4/semantic/similarity/train", data={ "api_key": "<api_key>", "model_id":"<model_id>"})

#for checking status of training

response = requests.post("https://apis.paralleldots.com/v4/semantic/similarity/train", data={ "api_key": "<api_key>", "model_id":"<model_id>","operation_code":"status"})

print(response.json())

```

```shell


curl -X POST -F "api_key=<api_key>" -F "model_id=<model_id>" https://apis.paralleldots.com/v4/semantic/similarity/train

# for status of training

curl -X POST -F "api_key=<api_key>" -F "model_id=<model_id>" -F "operation_code=status" https://apis.paralleldots.com/v4/semantic/similarity/train

```

```java
import java.io.IOException;
import okhttp3.OkHttpClient;
import okhttp3.Request;
import okhttp3.Response;
import okhttp3.MediaType;
import okhttp3.MultipartBody;
import okhttp3.RequestBody;
import okhttp3.ResponseBody;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;

String api_key = "<api_key>";
String model_id = "<model_id>";
String url = "https://apis.paralleldots.com/v4/semantic/similarity/train";
    OkHttpClient client = new OkHttpClient();
            RequestBody requestBody = new MultipartBody.Builder()
            .setType(MultipartBody.FORM)
            .addFormDataPart("api_key", api_key)
            .addFormDataPart("model_id", model_id)
            .build();
            Request request = new Request.Builder()
              .url(url)
              .post(requestBody)
              .addHeader("cache-control", "no-cache")
              .build();
Response response = client.newCall(request).execute();
System.out.println(response.body().string());

// for checking status of training

String operation_code = "status";
String api_key = "<api_key>";
String model_id = "<model_id>";
String url = "https://apis.paralleldots.com/v4/semantic/similarity/train";
    OkHttpClient client = new OkHttpClient();
            RequestBody requestBody = new MultipartBody.Builder()
            .setType(MultipartBody.FORM)
            .addFormDataPart("api_key", api_key)
            .addFormDataPart("model_id", model_id)
            .addFormDataPart("operation_code", operation_code)
            .build();
            Request request = new Request.Builder()
              .url(url)
              .post(requestBody)
              .addHeader("cache-control", "no-cache")
              .build();
Response response = client.newCall(request).execute();
System.out.println(response.body().string());
 
```

```php
<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://apis.paralleldots.com/v4/semantic/similarity/train",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data;  name=\"model_id\"\r\n\r\n<model_id>\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"api_key\"\r\n\r\n<api_key>\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
  CURLOPT_HTTPHEADER => array(
    "Cache-Control: no-cache",
    "content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW"
  ),
));

// for checking status of training

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://apis.paralleldots.com/v4/semantic/similarity/train",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data;  name=\"model_id\"\r\n\r\n<model_id>\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data;  name=\"operation_code\"\r\n\r\nstatus\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"api_key\"\r\n\r\n<api_key>\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
  CURLOPT_HTTPHEADER => array(
    "Cache-Control: no-cache",
    "content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}

```

```csharp
using System;
using Newtonsoft.Json.Linq;
using RestSharp;
using System.IO;


var api_key = "<api_key>";
var model_id = "<model_id>";
var url = "https://apis.paralleldots.com/v4/semantic/similarity/train";
var client = new RestClient(url);
var request = new RestRequest(Method.POST);
request.AddHeader("api_key",api_key );
request.AddHeader("model_id",model_id );
request.AddHeader("cache-control", "no-cache");
request.AddHeader("content-type", "application/json");
request.AddHeader("source", "c#wrapper");
IRestResponse response = client.Execute(request);
Console.WriteLine( response.Content.ToString());

// for checking status of training

var api_key = "<api_key>";
var model_id = "<model_id>";
var operation_code = "status";
var url = "https://apis.paralleldots.com/v4/semantic/similarity/train";
var client = new RestClient(url);
var request = new RestRequest(Method.POST);
request.AddHeader("api_key",api_key );
request.AddHeader("model_id",model_id );
request.AddHeader("operation_code",operation_code );
request.AddHeader("cache-control", "no-cache");
request.AddHeader("content-type", "application/json");
request.AddHeader("source", "c#wrapper");
IRestResponse response = client.Execute(request);
Console.WriteLine( response.Content.ToString());

```

```r
library("httr")
library("jsonlite")

url="https://apis.paralleldots.com/v4/semantic/similarity/train"
model_id='<model_id>'
api_key="<api_key>"

req <- POST(url,
              body = list(
                api_key=api_key,
                model_id=model_id
              ),
              encode = "multipart"
  )
stop_for_status(req)
result<-content(req)
print (toJSON(result, auto_unbox = TRUE))

#   for checking status of training 

model_id='<model_id>'
api_key="<api_key>"
operation_code="status"
req <- POST(url,
              body = list(
                api_key=api_key,
                model_id=model_id,
                operation_code=operation_code
              ),
              encode = "multipart"
  )
stop_for_status(req)
result<-content(req)
print (toJSON(result, auto_unbox = TRUE))


```
> The above command returns JSON structured like this:

```json

{
  "status": "Your model trainning in progress",
  
  "code":200
}

// for status of training

{
  "model trainned of documents": 100,
  
  "code":200
}

```

### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/semantic/similarity/train

`***POST*** /train` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| api_key | query | API key | Yes | string |
| model_id | query | a unique id to identify your model | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| number of document |  number of document train  | numeric |


## ***/predict***
**POST**

**Discription:**  Predict API allows to get similar ids of documents similar to an input document from your trained model. This API accept four parameter - text, n (number of similar documents you want), model_id, api_key and return json data containing array of similar documets id and their similarity score. 

```ruby
require 'rest-client'
require 'open-uri'
require 'json'
response = RestClient.post "https://apis.paralleldots.com/v4/semantic/similarity/predict", { api_key: "<api_key>", model_id:"<model_id>",text:"Come on, lets play together",n:5}
response = JSON.parse( response )
puts response

```

```python
import requests
import json


response = requests.post("https://apis.paralleldots.com/v4/semantic/similarity/predict", data={ "api_key": "<api_key>", "model_id":"<model_id>","text":"Come on, lets play together","n":5})

print(response.json())

```

```shell


curl -X POST  -F  "api_key=<api_key>" -F "text=I love panads" -F "model_id=<model_id>" -F "n=5" https://apis.paralleldots.com/v4/semantic/similarity/predict 
```

```java
import java.io.IOException;
import okhttp3.OkHttpClient;
import okhttp3.Request;
import okhttp3.Response;
import okhttp3.MediaType;
import okhttp3.MultipartBody;
import okhttp3.RequestBody;
import okhttp3.ResponseBody;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;

String api_key = "<api_key>";
String model_id = "<model_id>";
int n= 5;
String text = "Come on, lets play together";
String url = "https://apis.paralleldots.com/v4/semantic/similarity/predict";
    OkHttpClient client = new OkHttpClient();
            RequestBody requestBody = new MultipartBody.Builder()
            .setType(MultipartBody.FORM)
            .addFormDataPart("api_key", api_key)
            .addFormDataPart("model_id", model_id)
            .addFormDataPart("text", text)
            .addFormDataPart("n",Integer.toString(n))
            .build();
            Request request = new Request.Builder()
              .url(url)
              .post(requestBody)
              .addHeader("cache-control", "no-cache")
              .build();
Response response = client.newCall(request).execute();
System.out.println(response.body().string());
 
```

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://apis.paralleldots.com/v4/semantic/similarity/predict",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data;  name=\"model_id\"\r\n\r\n<model_id>\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data;
  name=\"text\"\r\n\r\nCome on, lets play together\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data;
  name=\"n\"\r\n\r\n5\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data;
  name=\"api_key\"\r\n\r\n<api_key>\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
  CURLOPT_HTTPHEADER => array(
    "Cache-Control: no-cache",
    "content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}

```

```csharp
using System;
using Newtonsoft.Json.Linq;
using RestSharp;
using System.IO;

var api_key = "<api_key>";
var model_id = "<model_id>";
var text = "Come on, lets play together";
var n=5;
var url = "https://apis.paralleldots.com/v4/semantic/similarity/predict";
var client = new RestClient(url);
var request = new RestRequest(Method.POST);
request.AddHeader("api_key",api_key );
request.AddHeader("model_id",model_id );
request.AddHeader("n",n );
request.AddHeader("text",text );
request.AddHeader("cache-control", "no-cache");
request.AddHeader("content-type", "application/json");
request.AddHeader("source", "c#wrapper");
IRestResponse response = client.Execute(request);
Console.WriteLine( response.Content.ToString());
```

```r
library("httr")
library("jsonlite")

url="https://apis.paralleldots.com/v4/semantic/similarity/predict"
model_id='<model_id>'
api_key="<api_key>"
text="Come on, lets play together"
n=5

req <- POST(url,
              body = list(
                api_key=api_key,
                model_id=model_id,
                text=text
                n=n
              ),
              encode = "multipart"
  )
  stop_for_status(req)
  result<-content(req)
  print (toJSON(result, auto_unbox = TRUE))

```
> The above command returns JSON structured like this:

```json
{
    "output": [
        {
            "id": 1,
            "similarity_score": 1
        },
        {
            "id": 4,
            "similarity_score": 1
        },
        {
            "id": 2,
            "similarity_score": 1
        }
    ],
    "code": 200
}

```



### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/semantic/similarity/predict

`***POST*** /predict` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| api_key | query | API key | Yes | string |
| model_id | query | a unique id to identify your model | Yes | string |
| n | query | number of similar documents required | Yes | string |
| text | query | Input document of which you need similar documents | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| id | similar documents id | numeric |
| similarity score | similarity score of document in model | float |



## ***/id2document***
**POST**

**Discription:** Id2Document API to find documents corresponding to their id and accept parameter - model_id, api_key and documents_id and return json response with document id and the corresponding document.

```ruby

document_id=[1,4,2]
document_id = document_id.to_json
response = RestClient.post "https://apis.paralleldots.com/v4/semantic/similarity/id2document", { api_key: "<api_key>", model_id:"<model_id>", document_id:document_id}
response = JSON.parse( response )
puts response

```

```python
import requests
import json


response = requests.post("https://apis.paralleldots.com/v4/semantic/similarity/id2document", data={ "api_key": "<api_key>", "model_id":"<model_id>", "document_id"=json.dumps([1,4,2])})

print(response.json())

```

```shell


curl -X POST -F 'api_key=<api_key>' -F 'model_id=<model_id>' -F 'document_id=[1,4,2]' https://apis.paralleldots.com/v4/semantic/similarity/id2document
```

```java
import java.io.IOException;
import okhttp3.OkHttpClient;
import okhttp3.Request;
import okhttp3.Response;
import okhttp3.MediaType;
import okhttp3.MultipartBody;
import okhttp3.RequestBody;
import okhttp3.ResponseBody;

import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;

String api_key = "<api_key>";
String model_id = "<model_id>";
JSONParser parser = new JSONParser();
JSONArray text_list = (JSONArray)parser.parse("[1,4,2]");
String url = "https://apis.paralleldots.com/v4/semantic/similarity/id2document";
    OkHttpClient client = new OkHttpClient();
            RequestBody requestBody = new MultipartBody.Builder()
            .setType(MultipartBody.FORM)
            .addFormDataPart("api_key", api_key)
            .addFormDataPart("model_id", model_id)
            .addFormDataPart("document_id", text_list.toString())
            .build();
            Request request = new Request.Builder()
              .url(url)
              .post(requestBody)
              .addHeader("cache-control", "no-cache")
              .build();
Response response = client.newCall(request).execute();
System.out.println(response.body().string());
 
```

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://apis.paralleldots.com/v4/semantic/similarity/id2document",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data;  name=\"model_id\"\r\n\r\n<model_id>\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data;
  name=\"document_id\"\r\n\r\n[1,4,2]\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"api_key\"\r\n\r\n<api_key>\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
  CURLOPT_HTTPHEADER => array(
    "Cache-Control: no-cache",
    "content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}

```

```csharp
using System;
using Newtonsoft.Json.Linq;
using RestSharp;
using System.IO;
JObject id_array = JObject.Parse(@"[1,4,2]");

var api_key = "<api_key>";
var model_id = "<model_id>";
var url = "https://apis.paralleldots.com/v4/semantic/similarity/id2document";
var client = new RestClient(url);
var request = new RestRequest(Method.POST);
request.AddHeader("api_key",api_key );
request.AddHeader("model_id",model_id );
request.AddHeader("document_id",id_array );
request.AddHeader("cache-control", "no-cache");
request.AddHeader("content-type", "application/json");
request.AddHeader("source", "c#wrapper");
IRestResponse response = client.Execute(request);
Console.WriteLine( response.Content.ToString());
```

```r
library("httr")
library("jsonlite")

url="https://apis.paralleldots.com/v4/semantic/similarity/id2document"
model_id='<model_id>'
string_id='[1,4,2]'
api_key="<api_key>"
req <- POST(url,
              body = list(
                api_key=key,
                model_id=model_id,
                document_id=string_id
              ),
              encode = "multipart"
  )
  stop_for_status(req)
  result<-content(req)
  print (toJSON(result, auto_unbox = TRUE))
}
```
> The above command returns JSON structured like this:

```json
{
  "1": "Come on, lets play together",
  "2": "Come on, lets play together",
  "4": "Come on, lets play together",
  
  "code":200
}

```



### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/semantic/similarity/id2document

`***POST*** /id2document` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| document_id | query | Pass a statement | Yes | list of document id |
| api_key | query | API key | Yes | string |
| model_id | query | a unique id to identify your model | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| document_id |  documents corresponding to their document id   | array |

## ***/model/property***
**POST**

**Discription:** model_property API allows to see all model status which you create. It accepts one parameters- api_key. 
Return json data containing model_id, number of documents trained and untrained data of that model

```ruby
require 'rest-client'
require 'open-uri'
require 'json'


response = RestClient.post "https://apis.paralleldots.com/v4/semantic/similarity/model/property", { api_key: "<api_key>"}
response = JSON.parse( response )
puts response

```

```python
import requests
import json


response = requests.post("https://apis.paralleldots.com/v4/semantic/similarity/model/property", data={ "api_key": "<api_key>"})

print(response.json())

```

```shell
curl -X POST -F 'api_key=<api_key>'  https://apis.paralleldots.com/v4/semantic/similarity/model/property
```

```java
import java.io.IOException;
import okhttp3.OkHttpClient;
import okhttp3.Request;
import okhttp3.Response;
import okhttp3.MediaType;
import okhttp3.MultipartBody;
import okhttp3.RequestBody;
import okhttp3.ResponseBody;
import org.json.simple.JSONArray;
import org.json.simple.parser.JSONParser;

String api_key = "<api_key>";
String url = "https://apis.paralleldots.com/v4/semantic/similarity/model/property";
    OkHttpClient client = new OkHttpClient();
            RequestBody requestBody = new MultipartBody.Builder()
            .setType(MultipartBody.FORM)
            .addFormDataPart("api_key", api_key)
            .build();
            Request request = new Request.Builder()
              .url(url)
              .post(requestBody)
              .addHeader("cache-control", "no-cache")
              .build();
Response response = client.newCall(request).execute();
System.out.println(response.body().string());
 
```

```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => "https://apis.paralleldots.com/v4/semantic/similarity/model/property",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data;  name=\"api_key\"\r\n\r\n<api_key>\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
  CURLOPT_HTTPHEADER => array(
    "Cache-Control: no-cache",
    "content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}

```

```csharp
using System;
using Newtonsoft.Json.Linq;
using RestSharp;
using System.IO;

var api_key = "<api_key>"
var url = "https://apis.paralleldots.com/v4/semantic/similarity/model/property";
var client = new RestClient(url);
var request = new RestRequest(Method.POST);
request.AddParameter("api_key", api_key);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("content-type", "application/json");
request.AddHeader("source", "c#wrapper");
IRestResponse response = client.Execute(request);
Console.WriteLine( response.Content.ToString());
```

```r
library("httr")
library("jsonlite")

url="https://apis.paralleldots.com/v4/semantic/similarity/model/property"
api_key="<api_key>"
req <- POST(url,
              body = list(
                api_key=api_key
              ),
              encode = "multipart"
  )
  stop_for_status(req)
  result<-content(req)
  print (toJSON(result, auto_unbox = TRUE))

```
> The above command returns JSON structured like this:

```json
{
    "output": [
        {
            "model_id": "xxxxxx",
            "number of trained documents": 10000,
            "number of untrained documents ": 500
        },
        {
            "model_id": "xxxxxx",
            "number of trained documents": 2000,
            "number of untrained documents ": 100
        }
    ],
    "code": 200
}

```

### HTTP Request 

**Endpoint** https://apis.paralleldots.com/v4/semantic/similarity/model/property

`***POST*** /model/property` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| api_key | query | API key | Yes | string |

**Responses**

| Name | Description | Type |
| ---- | ----------- | ---- |
| model_id | a unique id to identify your model | string |
| number of trained documents | trained documents | numeric |
| number of untrained documents | untrained documents | numeric |


**HTTP Error Codes**

| Code | Text | Description |
| ---- | ---- | ----------- |
| 200 |OK| Successful response |
| 304 |Not Modified| There was no new text to return. |
| 500 |Internal Server Error| Backend Error. |
| 400 |Bad Request| Please provide valid input parameter. |
| 401 |Unauthorized| Invalid Credentials and model id. Please provide valid API key and model id|
| 403 |Forbidden| Daily/Monthy Limit Exceeded. Please upgrade your account from your user dashboard at <a href="https://user.apis.paralleldots.com/user_dashboard">https://user.apis.paralleldots.com/user_dashboard</a>  |
| 429 |Too Many Requests| Too Many Requests. Please try after sometime. |
| 406 |Not Acceptable| Invalid Format. Parameter text should be string |
lid Format. Parameter text should be string |


<!-- Converted with the swagger-to-slate https://github.com/lavkumarv/swagger-to-slate -->
