---
id: inbox_160e0010
source: simon-willison
source_type: rss
url: "https://simonwillison.net/2026/May/24/datasette-fixtures/#atom-everything"
author: ""
published_at: 2026-05-24T21:38:32+00:00
fetched_at: 2026-05-25T00:11:34.621809+00:00
content_hash: "edeaaa57d74434527e1eb8269212d158d74cb3fc686681e3b082a8e832eeba3f"
lang: en
caption_quality: None
raw: true
topics: []
---

# datasette-fixtures 0.1a0

Release: datasette-fixtures 0.1a0 
 One of the smaller features in Datasette 1.0a30 is this: 
 
 New documented datasette.fixtures.populate_fixture_database(conn) helper for creating the fixture database tables used by Datasette's own tests, intended for plugin test suites. 
 
 This new plugin takes advantage of that API. You can try it out using uvx without even installing Datasette like this: 
 uvx --prerelease=allow \
 --with datasette-fixtures datasette \
 --get /fixtures/roadside_attractions.json 
 Which outputs: 
 {
 "ok" : true ,
 "next" : null ,
 "rows" : [
 { "pk" : 1 , "name" : " The Mystery Spot " , "address" : " 465 Mystery Spot Road, Santa Cruz, CA 95065 " , "url" : " https://www.mysteryspot.com/ " , "latitude" : 37.0167 , "longitude" : -122.0024 },
 { "pk" : 2 , "name" : " Winchester Mystery House " , "address" : " 525 South Winchester Boulevard, San Jose, CA 95128 " , "url" : " https://winchestermysteryhouse.com/ " , "latitude" : 37.3184 , "longitude" : -121.9511 },
 { "pk" : 3 , "name" : " Burlingame Museum of PEZ Memorabilia " , "address" : " 214 California Drive, Burlingame, CA 94010 " , "url" : null , "latitude" : 37.5793 , "longitude" : -122.3442 },
 { "pk" : 4 , "name" : " Bigfoot Discovery Museum " , "address" : " 5497 Highway 9, Felton, CA 95018 " , "url" : " https://www.bigfootdiscoveryproject.com/ " , "latitude" : 37.0414 , "longitude" : -122.0725 }
 ],
 "truncated" : false 
} 
 
 
 Tags: datasette , uv