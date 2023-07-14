[1]: https://rosettacode.org/wiki/Playing_cards

# [Playing cards][1]

```ruby
define Pip = <A 2 3 4 5 6 7 8 9 10 J Q K>;
define Suit = <♦ ♣ ♥ ♠>;
 
class Card(pip, suit) {
    method to_s { pip + suit }
}
 
class Deck(cards=[]) {
 
    method init {
        cards = gather {
            Pip.each { |p| Suit.each { |s| take(Card(p, s)) } }
        }
    }
 
    method shuffle {
        cards.shuffle!;
    }
 
    method deal { cards.shift };
    method to_s { cards.join(" ") };
}
 
var d = Deck();
say "Deck: #{d}";
 
var top = d.deal;
say "Top card: #{top}";
 
d.shuffle;
say "Deck, shuffled: #{d}";
```

#### Output:
```
Deck: A♦ A♣ A♥ A♠ 2♦ 2♣ 2♥ 2♠ 3♦ 3♣ 3♥ 3♠ 4♦ 4♣ 4♥ 4♠ 5♦ 5♣ 5♥ 5♠ 6♦ 6♣ 6♥ 6♠ 7♦ 7♣ 7♥ 7♠ 8♦ 8♣ 8♥ 8♠ 9♦ 9♣ 9♥ 9♠ 10♦ 10♣ 10♥ 10♠ J♦ J♣ J♥ J♠ Q♦ Q♣ Q♥ Q♠ K♦ K♣ K♥ K♠
Top card: A♦
Deck, shuffled: 10♠ 2♠ 3♠ Q♥ 3♣ A♠ 6♠ 6♣ 9♣ 6♦ Q♦ 8♣ 4♦ 7♠ 10♦ 3♥ 4♠ 7♥ 8♠ 10♥ 10♣ 9♦ 5♠ Q♠ A♥ 4♥ J♥ Q♣ 7♣ 2♥ 6♥ 8♥ 5♥ 7♦ J♠ 5♦ K♦ 3♦ J♣ 2♦ 5♣ K♥ 9♥ 2♣ 8♦ A♣ K♣ 9♠ K♠ J♦ 4♣
```