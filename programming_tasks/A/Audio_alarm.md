[1]: https://rosettacode.org/wiki/Audio_alarm

# [Audio alarm][1]

Requires mpg123 to be installed.

```ruby
var seconds = Sys.read("Enter a number of seconds: ", Number)
var mp3filepath = Sys.read("Enter a MP3 file to be played: ", File)+".mp3"
Sys.sleep(seconds)
Sys.run('mpg123', '-q', mp3filepath)
```
