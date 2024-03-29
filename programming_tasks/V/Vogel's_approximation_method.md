[1]: https://rosettacode.org/wiki/Vogel's_approximation_method

# [Vogel's approximation method][1]

```ruby
var costs = :(
    W => :(A => 16, B => 16, C => 13, D => 22, E => 17),
    X => :(A => 14, B => 14, C => 13, D => 19, E => 15),
    Y => :(A => 19, B => 19, C => 20, D => 23, E => 50),
    Z => :(A => 50, B => 12, C => 50, D => 15, E => 11)
)

var demand = :(A => 30, B => 20, C => 70, D => 30, E => 60)
var supply = :(W => 50, X => 60, Y => 50, Z => 50)

var cols = demand.keys.sort

var (:res, :g)
supply.each {|x| g{x} = costs{x}.keys.sort_by{|g| costs{x}{g} }}
demand.each {|x| g{x} = costs   .keys.sort_by{|g| costs{g}{x} }}

while (g) {
    var d = demand.collect {|x|
        [x, var z = costs{g{x}[0]}{x}, g{x}[1] ? costs{g{x}[1]}{x}-z : z]
    }

    var s = supply.collect {|x|
        [x, var z = costs{x}{g{x}[0]}, g{x}[1] ? costs{x}{g{x}[1]}-z : z]
    }

    d.grep! { .[2] == d.max_by{ .[2] }[2] }.min_by! { .[1] }
    s.grep! { .[2] == s.max_by{ .[2] }[2] }.min_by! { .[1] }

    var (t,f) = (d[2] == s[2] ? ((s[1], d[1])) : ((d[2], s[2])))
        (d,s) = (t > f ? ((d[0], g{d[0]}[0])) : ((g{s[0]}[0],s[0])))

    var v = (supply{s} `min` demand{d})

    res{s}{d} := 0 += v
    demand{d} -= v

    if (demand{d} == 0) {
        supply.grep {|_,n| n != 0 }.each {|x| g{x}.delete(d) }
        g.delete(d)
        demand.delete(d)
    }

    supply{s} -= v

    if (supply{s} == 0) {
        demand.grep {|_,n| n != 0 }.each {|x| g{x}.delete(s) }
        g.delete(s)
        supply.delete(s)
    }
}

say("\t", cols.join("\t"))

var cost = 0
costs.keys.sort.each { |g|
  print(g, "\t")
  cols.each { |n|
    if (defined(var y = res{g}{n})) {
        print(y)
        cost += (y * costs{g}{n})
    }
    print("\t")
  }
  print("\n")
}

say "\n\nTotal Cost = #{cost}"
```

#### Output:
```
        A       B       C       D       E
W                       50                      
X       30              20              10      
Y               20              30              
Z                                       50      


Total Cost = 3100
```
