[1]: https://rosettacode.org/wiki/Speech_synthesis

# [Speech synthesis][1]

```ruby
func text2speech(text, lang='en') {
    Sys.run("espeak -v #{lang} -w /dev/stdout #{text.escape} | aplay")
}
text2speech("This is an example of speech synthesis.")
```
