[1]: https://rosettacode.org/wiki/Guess_the_number/With_feedback_(player)

# [Guess the number/With feedback (player)][1]

```ruby
var min = 1
var max = 99
var tries = 0
var guess = pick(min..max)
 
print <<"EOT".chomp
\n=>> Think of a number between #{min} and #{max} and I'll guess it!\n
Press <ENTER> when are you ready...
EOT
 
STDIN.readline
 
loop {
    print <<-EOT.chomp
    \n=>> My guess is: #{guess} Is your number higher, lower, or equal? (h/l/e)
    >#{' '}
    EOT
 
    ++tries
    given (STDIN.readline) {
        case (max <= min) {
            say "\nI give up..."
            break
        }
        when (/^h/i) {
            min = guess+1
        }
        when (/^l/i) {
            max = guess
        }
        when (/^e/i) {
            say "\nI knew it! It took me only #{tries} tries."
            break
        }
        default {
            say "error: invalid score"
            next
        }
    }
 
    guess = ((min+max) // 2)
}
```
