[1]: https://rosettacode.org/wiki/Extend_your_language

# [Extend your language][1]

```ruby
class if2(cond1, cond2) {
    method then(block) {    # both true
        if (cond1 && cond2) {
            block.run;
        }
        return self;
    }
    method else1(block) {   # first true
        if (cond1 && !cond2) {
            block.run;
        }
        return self;
    }
    method else2(block) {   # second true
        if (cond2 && !cond1) {
            block.run;
        }
        return self;
    }
    method else(block) {    # none true
        if (!cond1 && !cond2) {
            block.run;
        }
        return self;
    }
}
 
if2(false, true).then {
    say "if2";
}.else1 {
    say "else1";
}.else2 {
    say "else2";        # <- this gets printed
}.else {
    say "else"
}
```