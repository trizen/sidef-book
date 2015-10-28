[1]: http://rosettacode.org/wiki/Bernoulli_numbers

# [Bernoulli numbers][1]

Recursive solution (with auto-memoization):

```ruby
func bernoulli_number{};     # must be declared before first used
 
func bern_helper(n, k) {
    binomial(n, k).rat * (bernoulli_number(k).rat / (n - k + 1));
}
 
func bern_diff(n, k, d) {
    n < k ? d : bern_diff(n, k + 1, d.rat - bern_helper(n + 1, k));
}
 
bernoulli_number = func(n) is cached {
 
    n.is_one && return 1/2;
    n.is_odd && return   0;
 
    n > 0 ? bern_diff(n - 1, 0, 1) : 1;
}
 
range(0, 60).each { |i|
    var num = bernoulli_number(i) || next;
    printf("B(%2d) = %44s / %s\n", i, num.to_r.parts);
}
```


Iterative solution:

```ruby
func bernoulli_print {
    var a = [];
    range(0, 60).each { |m|
        a.append(1.rat / rat(m+1));
        range(m, 1, -1).each { |j|
            a[j-1] = (j.rat * (a[j-1] - a[j]));
        }
        a[0] || next;
        printf("B(%2d) = %44s / %s\n", m, a[0].parts);
    }
}
 
bernoulli_print();
```

#### Output:
```
B( 0) =                                            1 / 1
B( 1) =                                            1 / 2
B( 2) =                                            1 / 6
B( 4) =                                           -1 / 30
B( 6) =                                            1 / 42
B( 8) =                                           -1 / 30
B(10) =                                            5 / 66
B(12) =                                         -691 / 2730
B(14) =                                            7 / 6
B(16) =                                        -3617 / 510
B(18) =                                        43867 / 798
B(20) =                                      -174611 / 330
B(22) =                                       854513 / 138
B(24) =                                   -236364091 / 2730
B(26) =                                      8553103 / 6
B(28) =                                 -23749461029 / 870
B(30) =                                8615841276005 / 14322
B(32) =                               -7709321041217 / 510
B(34) =                                2577687858367 / 6
B(36) =                        -26315271553053477373 / 1919190
B(38) =                             2929993913841559 / 6
B(40) =                       -261082718496449122051 / 13530
B(42) =                       1520097643918070802691 / 1806
B(44) =                     -27833269579301024235023 / 690
B(46) =                     596451111593912163277961 / 282
B(48) =                -5609403368997817686249127547 / 46410
B(50) =                  495057205241079648212477525 / 66
B(52) =              -801165718135489957347924991853 / 1590
B(54) =             29149963634884862421418123812691 / 798
B(56) =          -2479392929313226753685415739663229 / 870
B(58) =          84483613348880041862046775994036021 / 354
B(60) = -1215233140483755572040304994079820246041491 / 56786730
```