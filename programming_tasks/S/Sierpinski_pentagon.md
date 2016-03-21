[1]: http://rosettacode.org/wiki/Sierpinski_pentagon

# [Sierpinski pentagon][1]

Generates a SVG image to STDOUT. Redirect to a file to capture and display it.

```ruby
define order = 5
define sides = 5
define dim   = 500
define scaling_factor = ((3 - 5**0.5) / 2)
var orders = order.of {|i| ((1-scaling_factor) * dim) * scaling_factor**(i-1) }
 
say <<"STOP";
<?xml version="1.0" standalone="no"?>
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN"
    "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg height="#{dim*2}" width="#{dim*2}"
    style="fill:blue" transform="translate(#{dim},#{dim}) rotate(-18)"
    version="1.1" xmlns="http://www.w3.org/2000/svg">
STOP
 
var vertices = sides.of {|i| Complex(0, i * Number.tau / sides).exp }
 
(sides**order).range.each { |i|
   var vector = ([vertices.@["%#{order}d" % i.base(sides) -> chars]] »*« orders «+»)
   var points = (vertices »*» orders[-1]*(1-scaling_factor) »+» vector »reals»() «%« '%0.3f')
   say ('<polygon points="' + points.join(' ') + '"/>')
}
 
say '</svg>'
```