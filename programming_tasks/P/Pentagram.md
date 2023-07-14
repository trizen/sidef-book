[1]: https://rosettacode.org/wiki/Pentagram

# [Pentagram][1]

Generates a SVG image to STDOUT.

```ruby
func pentagram(dim=200, sides=5) {
    var pentagram = <<-EOT
    <?xml version="1.0" standalone="no" ?>
    <!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.0//EN"
    "http://www.w3.org/TR/2001/PR-SVG-20010719/DTD/svg10.dtd">
    <svg height="#{dim*2}" width="#{dim*2}" style="" xmlns="http://www.w3.org/2000/svg">
    <rect height="100%" width="100%" style="fill:black;" />
    EOT

    func pline(q) {
        <<-EOT
        <polyline points="#{{|n| '%0.3f' % n }.map(q, q[0], q[1]).join(' ')}"
        style="fill:blue; stroke:white; stroke-width:3;"
        transform="translate(#{dim}, #{dim}) rotate(-18)" />
        EOT
    }

    var v = {|k| 0.9 * dim * cis(k * Num.tau / sides) }.map(^sides)
    pentagram += pline([v[range(0, v.end, 2)], v[range(1, v.end, 2)]].map{.reals})
    pentagram += '</svg>'

    return pentagram
}

say pentagram()
```

#### Output:
```xml
<?xml version="1.0" standalone="no" ?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.0//EN"
"http://www.w3.org/TR/2001/PR-SVG-20010719/DTD/svg10.dtd">
<svg height="400" width="400" style="" xmlns="http://www.w3.org/2000/svg">
<rect height="100%" width="100%" style="fill:black;" />
<polyline points="180.000 0.000 -145.623 105.801 55.623 -171.190 55.623 171.190 -145.623 -105.801 180.000 0.000"
style="fill:blue; stroke:white; stroke-width:3;"
transform="translate(200, 200) rotate(-18)" />
</svg>
```
