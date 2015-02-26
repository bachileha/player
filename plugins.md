# Plugins

The Hola Player has plugin api for extending its functionality.
The following plugins are supported:
* Fetching subtitles (under development)
* Fetching poster (SOON)
* Fetching video description (SOON)
* More to come... Please submit requests for missing api.

### Subtitles XML-RPC plugin (subs-xmlrpc)
The subtitles XML-RPC plugin (subs-xmlrpc) connects to subtitles server using XML-RPC protocol and fetch the subtitles for the video. The video is matched against video id, video title and video hash (SOON).
```json
{
	"type": "subs-xmlrpc",
	"url": "http://hola.org/player/api/xml-rpc",
	"user_agent": "HolaTestUserAgent",
	"user": "",
	"password": "",
	"OPEN_VIDEO_ID.regex": "\\<a .*href=\".*hola\\.org.*/vid([0-9]+\\b)",
	"search_subtitles": {
		"by_id": {
			"vid": "{OPEN_VIDEO_ID}"
		},
		"by_free_text": {
			"query": "{OPEN_VIDEO_TITLE}"
		}
	}
}
```
#### Configuration
* `url` - set the url of your subtitle xml-rpc server
* `user_agent` - set the user_agent to your subtitle xml-rpc server user agent
* `OPEN_VIDEO_ID.regex` - this regex is run on the page html where the video resides. it is used to automtically extract the OPEN_VIDEO_ID for video identification. update it to match your page html syntax and video id format
* `search_subtitles.by_id` - if OPEN_VIDEO_ID is found, the plugin will execute SearchSubtitles function via XML-RPC with the following query: {vid: "{OPEN_VIDEO_ID}"}. You may need to change "vid" to your xml-rpc subtitles provider video id name.
* `search_subtitles.by_free_text` - if no OPEN_VIDEO_ID is found, the plugin will execute SearchSubtitles function via XML-RPX with the following query: {query: {OPEN_VIDEO_TITLE}}. You may need to change "vid" to your xml-rpc subtitles provider full text search option.


