[1]: https://rosettacode.org/wiki/Zebra_puzzle

# [Zebra puzzle][1]

```ruby
var CONTENT = Hash(
            :House       => nil,
            :Nationality => [:English, :Swedish, :Danish, :Norwegian, :German],
            :Colour      => [:Red, :Green, :White, :Blue, :Yellow],
            :Pet         => [:Dog, :Birds, :Cats, :Horse, :Zebra],
            :Drink       => [:Tea, :Coffee, :Milk, :Beer, :Water],
            :Smoke       => [:PallMall, :Dunhill, :BlueMaster, :Prince, :Blend]
)

func adjacent(n,i,g,e) {
  (0..3).any {|x| (n[x]==i && g[x+1]==e) || (n[x+1]==i && g[x]==e) }
}

func leftof(n,i,g,e) {
  (0..3).any {|x| n[x]==i && g[x+1]==e }
}

func coincident(n,i,g,e) {
  n.indices.any {|x| n[x]==i && g[x]==e }
}

func solve {
  CONTENT{:Nationality}.permutations{|*nation|
    nation.first == :Norwegian ->
      && CONTENT{:Colour}.permutations {|*colour|
          leftof(colour,:Green,colour,:White) ->
       && coincident(nation,:English,colour,:Red) ->
       && adjacent(nation,:Norwegian,colour,:Blue) ->
       && CONTENT{:Pet}.permutations {|*pet|
             coincident(nation,:Swedish,pet,:Dog) ->
          && CONTENT{:Drink}.permutations {|*drink|
               drink[2] == :Milk ->
            && coincident(nation,:Danish,drink,:Tea) ->
            && coincident(colour,:Green,drink,:Coffee) ->
            && CONTENT{:Smoke}.permutations {|*smoke|
                coincident(smoke,:PallMall,pet,:Birds) ->
             && coincident(smoke,:Dunhill,colour,:Yellow) ->
             && coincident(smoke,:BlueMaster,drink,:Beer) ->
             && coincident(smoke,:Prince,nation,:German) ->
             && adjacent(smoke,:Blend,pet,:Cats) ->
             && adjacent(smoke,:Blend,drink,:Water) ->
             && adjacent(smoke,:Dunhill,pet,:Horse) ->
             && return [nation,colour,pet,drink,smoke]
} } } } } }

var res = solve();
var keys = [:House, :Nationality, :Colour, :Pet, :Drink, :Smoke]
var width = keys.map{ .len }
var fmt = width.map{|w| "%-#{w+2}s" }.join(" ")
say "The Zebra is owned by the man who is #{res[0][res[2].first_index(:Zebra)]}\n"
say (fmt % keys..., "\n", fmt % width.map{|w| "-"*w }...)
res[0].indices.map{|i| res.map{|a| a[i] }}.each_kv {|k,v| say fmt%(k,v...) }
```

#### Output:
```
The Zebra is owned by the man who is German

House   Nationality   Colour   Pet   Drink   Smoke
-----   -----------   ------   ---   -----   -----
0       Norwegian     Yellow   Cats  Water   Dunhill
1       Danish        Blue     Horse Tea     Blend
2       English       Red      Birds Milk    PallMall
3       German        Green    Zebra Coffee  Prince
4       Swedish       White    Dog   Beer    BlueMaster
```
