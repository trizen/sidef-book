[1]: http://rosettacode.org/wiki/Digital_root

# [Digital root][1]

```ruby
func digroot (r, base = 10) {
    var root = r.base(base)
    var persistence = 0
    while (root.len > 1) {
        root = root.chars.map{|n| Number(n, 36) }.sum(0).base(base)
        ++persistence
    }
    return(persistence, root)
}
 
var nums = [5, 627615, 39390, 588225, 393900588225]
var bases = [2, 3, 8, 10, 16, 36]
var fmt = "%25s(%2s): persistance = %s, root = %2s\n"
 
nums << (550777011503 *
         105564897893993412813307040538786690718089963180462913406682192479)
 
bases.each { |b|
    nums.each { |n|
        var x = n.base(b)
        x = 'BIG' if (x.len > 25)
        fmt.printf(x, b, digroot(n, b))
    }
    print "\n"
}
```

#### Output:
```
                      101( 2): persistance = 2, root =  1
     10011001001110011111( 2): persistance = 3, root =  1
         1001100111011110( 2): persistance = 3, root =  1
     10001111100111000001( 2): persistance = 3, root =  1
                      BIG( 2): persistance = 3, root =  1
                      BIG( 2): persistance = 4, root =  1

                       12( 3): persistance = 2, root =  1
            1011212221000( 3): persistance = 3, root =  1
               2000000220( 3): persistance = 2, root =  2
            1002212220010( 3): persistance = 3, root =  1
1101122201121110011000000( 3): persistance = 3, root =  1
                      BIG( 3): persistance = 4, root =  1

                        5( 8): persistance = 0, root =  5
                  2311637( 8): persistance = 3, root =  2
                   114736( 8): persistance = 3, root =  1
                  2174701( 8): persistance = 3, root =  1
            5566623376301( 8): persistance = 3, root =  4
                      BIG( 8): persistance = 3, root =  3

                        5(10): persistance = 0, root =  5
                   627615(10): persistance = 2, root =  9
                    39390(10): persistance = 2, root =  6
                   588225(10): persistance = 2, root =  3
             393900588225(10): persistance = 2, root =  9
                      BIG(10): persistance = 3, root =  4

                        5(16): persistance = 0, root =  5
                    9939f(16): persistance = 2, root =  f
                     99de(16): persistance = 2, root =  f
                    8f9c1(16): persistance = 2, root =  f
               5bb64dfcc1(16): persistance = 2, root =  f
                      BIG(16): persistance = 3, root =  7

                        5(36): persistance = 0, root =  5
                     dg9r(36): persistance = 2, root =  u
                      ue6(36): persistance = 2, root =  f
                     clvl(36): persistance = 2, root =  f
                 50ye8n29(36): persistance = 2, root =  p
                      BIG(36): persistance = 3, root =  h
```