API documentation
=================

This API allows users to search and download video clips from a [Clip.Cafe](https://clip.cafe/) database, ideal for media platforms, educational content providers,  archival researchers, content creators, youtubers,tiktokers etc... 
Every request must have parameter api-key for authentication. You can obtain it [here](https://clip.cafe/api-keys/) (PRO subscription is required)

Authentication
--------------

### API Key

*   Required: An API key is necessary for all requests.
*   Usage: Include api\_key=YOUR\_API\_KEY in the query string.
*   Security: Treat your API key as sensitive information to prevent unauthorized access.
*   All integers can be used as ranges (e.g., 2005-2010 or 2005- or -2005).

Base URL
--------

All API requests should be initiated to: https://api.clip.cafe/.

Rate Limits
-----------

**PRO:** 10 requests per minute, up to 2000 requests and 1000 downloads per month. **PRO+:** 60 requests per minute, up to 10000 requests and 5000 downloads per month.

Search Video Clips
------------------

**Method:** GET **Purpose:** Retrieves video clips based on specified search criteria **Response:** JSON object containing an array of clips with detailed metadata.

### Query Parameters:

*   api\_key (string) YOUR\_API\_KEY (mandatory).
*   title (string) Search by video title.
*   actors (string) Search by actors' names.
*   characters (string) Search by character's names.
*   slug (string) Search by unique slug.
*   transcript (string) Search within video transcripts.
*   imdb (string) Search by IMDb identifier.
*   movie\_imdbscore (string) Search by IMDb score.
*   movie\_metascore (string) Search by Meta Score.
*   movie\_director (string) Search by director's name.
*   movie\_writer (string) Search by writer's name.
*   movie\_title (string) Search by movies title.
*   movie\_slug (string) Search by movie slug.
*   movie\_actors (string) Search by actors in movie.
*   movie\_summary (string) Search by movie summary.
*   movie\_slug (string) Search by movie slug.
*   sort (string) Sort results by a specific field (asc or desc. Default: score).
*   movie\_year (int) Filter by release year. Range queries allowed (e.g., 2005-2010).
*   duration (int) Filter by clip duration in seconds. Range queries allowed.
*   views (int) Filter by number of views. Range queries allowed.
*   likes (int) Filter by number of likes. Range queries allowed.
*   clipID (int) Search by specific clip ID. Range queries allowed.
*   season (int) Filter by TV show season number. Range queries allowed.
*   episode (int) Filter by TV show episode number. Range queries allowed.
*   size (int) Number of results to return per page. (Default: 10)
*   from (int) Offset for results (used for pagination).(Default: 0)

### Example Request:

GET /?api\_key=YOUR\_API\_KEY&duration=3&movie\_title=matrix&actors=keanu+reeves HTTP/1.1 Host: api.clip.cafe

### Response:

{ "took": 1, "timed\_out": false, "\_shards": { "total": 1, "successful": 1, "skipped": 0, "failed": 0 }, "hits": { "total": { "value": 2, "relation": "eq" }, "max\_score": 21.314917, "hits": \[ { "\_index": "videoclips", "\_id": "369707", "\_score": 21.314917, "\_source": { "clipID": 369707, "title": "Oh my God", "imdb": "tt0234215", "slug": "oh-god-s142", "transcript": "\[Johnson blocks Neo's punch\]\\n\\nNeo:\\nHmm, upgrades. | Oh my God", "episode": 0, "season": 0, "duration": 3, "views": 75, "likes": 0, "resolution": "1920x800", "date": "2022-11-25 09:25:10", "subtitles": "{\\"1\\":{\\"TimeStart\\":1,\\"TimeEnd\\":2.042,\\"Text\\":\\"Oh my God\\"}}", "actors": "Keanu Reeves,", "characters": "Neo,", "movie\_title": "The Matrix Reloaded", "movie\_writer": "Lilly Wachowski, Lana Wachowski", "movie\_director": "Lana Wachowski, Lilly Wachowski", "movie\_summary": "Freedom fighters Neo, Trinity and Morpheus continue to lead the revolt against the Machine Army, unleashing their arsenal of extraordinary skills and weaponry against the systematic forces of repression and exploitation.", "movie\_actors": null, "movie\_year": 2003, "movie\_poster": "https://m.media-amazon.com/images/M/MV5BODE0MzZhZTgtYzkwYi00YmI5LThlZWYtOWRmNWE5ODk0NzMxXkEyXkFqcGdeQXVyNjU0OTQ0OTY@.\_V1\_SX500.jpg", "movie\_postersize": "300x450", "movie\_imdbscore": "7.2", "movie\_metascore": "62", "movie\_slug": "the-matrix-reloaded-2003", "download": "https://api.clip.cafe/?api\_key=9951d6edc5744ee6c09b04132edefd00&key=210d559e4a489f83ace520e2ab383cc2a456c9410d7f164ba5b0681e1c287fb5&slug=oh-god-s142" } }, { "\_index": "videoclips", "\_id": "325832", "\_score": 16.717422, "\_source": { "clipID": 325832, "title": "Have we met", "imdb": "tt10838180", "slug": "have-met-s1", "transcript": "Neo:\\nHi! \\nTrinity:\\n...Have we met? | Have we met", "episode": 0, "season": 0, "duration": 3, "views": 43, "likes": 0, "resolution": "1920x804", "date": "2022-11-19 01:11:53", "subtitles": "{\\"1\\":{\\"TimeStart\\":1,\\"TimeEnd\\":2.126,\\"Text\\":\\"Have we met\\"}}", "actors": "Keanu Reeves,Carrie-Anne Moss,", "characters": "Neo,Trinity,", "movie\_title": "The Matrix Resurrections", "movie\_writer": "Lana Wachowski, David Mitchell, Aleksandar Hemon", "movie\_director": "Lana Wachowski", "movie\_summary": "Return to a world of two realities: one, everyday life; the other, what lies behind it. To find out if his reality is a construct, to truly know himself, Mr. Anderson will have to choose to follow the white rabbit once more.", "movie\_actors": null, "movie\_year": 2021, "movie\_poster": "https://m.media-amazon.com/images/M/MV5BMGJkNDJlZWUtOGM1Ny00YjNkLThiM2QtY2ZjMzQxMTIxNWNmXkEyXkFqcGdeQXVyMDM2NDM2MQ@@.\_V1\_SX500.jpg", "movie\_postersize": "500x741", "movie\_imdbscore": "5.7", "movie\_metascore": "63", "movie\_slug": "the-matrix-resurrections-2021", "download": "https://api.clip.cafe/?api\_key=9951d6edc5744ee6c09b04132edefd00&key=c7ec346bfeb041951cca8e77c37121e6bc3b32e00d83a760f9fc344a4746eab3&slug=have-met-s1" } } \] } }  

Download Video Clips
--------------------

**Method:** GET **Purpose:** Download a specific video clip. **Response:** Binary stream of the video clip.

### Query Parameters:

*   api\_key (string) YOUR\_API\_KEY (mandatory).
*   slug (string) Unique identifier for the clip (mandatory).
*   key (string) Unique download key (mandatory).

### Example Request:

GET /?api\_key=YOUR\_API\_KEY&slug=clip-slug&key=DOWNLOAD\_KEY HTTP/1.1 Host: api.clip.cafe

Error Codes
-----------

*   200 OK: Successful request.
*   400 Bad Request: Invalid request format or parameters.
*   401 Unauthorized: Missing or invalid API key.
*   403 Forbidden: Access denied.
*   404 Not Found: Resource not found.
*   429 Too Many Requests: Rate limit exceeded.
*   500 Internal Server Error: Server error.
