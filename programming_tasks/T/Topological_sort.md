[1]: http://rosettacode.org/wiki/Topological_sort

# [Topological sort][1]

```ruby
func print_topo_sort (deps) {
    var ba = Hash.new;
    deps.each { |before, afters|
        afters.each { |after|
            if (before != after) {
                ba{before}{after} = 1;
            };
            ba{after} \\= Hash.new;
        }
    };
 
    loop {
        var afters = ba.keys.grep {|k| ba{k}.values.len == 0 }.sort;
        afters.len || break;
        say afters.join(" ");
        ba.delete(afters...);
        ba.values.each { |v| v.delete(afters...) };
    };
 
    say (ba.len ? "Cicle found! #{ba.keys.sort}" : "---");
}
 
var deps = Hash.new(
    des_system_lib => < std synopsys std_cell_lib des_system_lib dw02
                                                     dw01 ramlib ieee >,
    dw01           => < ieee dw01 dware gtech                         >,
    dw02           => < ieee dw02 dware                               >,
    dw03           => < std synopsys dware dw03 dw02 dw01 ieee gtech  >,
    dw04           => < dw04 ieee dw01 dware gtech                    >,
    dw05           => < dw05 ieee dware                               >,
    dw06           => < dw06 ieee dware                               >,
    dw07           => < ieee dware                                    >,
    dware          => < ieee dware                                    >,
    gtech          => < ieee gtech                                    >,
    ramlib         => < std ieee                                      >,
    std_cell_lib   => < ieee std_cell_lib                             >,
    synopsys       => <                                               >
);
 
print_topo_sort(deps);
deps{:dw01}.append('dw04');     # Add unresolvable dependency
print_topo_sort(deps);
```

#### Output:
```
ieee std synopsys
dware gtech ramlib std_cell_lib
dw01 dw02 dw05 dw06 dw07
des_system_lib dw03 dw04
---
ieee std synopsys
dware gtech ramlib std_cell_lib
dw02 dw05 dw06 dw07
Cicle found! des_system_lib dw01 dw03 dw04
```