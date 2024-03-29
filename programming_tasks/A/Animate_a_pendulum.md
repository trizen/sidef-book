[1]: https://rosettacode.org/wiki/Animate_a_pendulum

# [Animate a pendulum][1]

```ruby
require('Tk')
 
var root = %O<MainWindow>.new('-title' => 'Pendulum Animation')
var canvas = root.Canvas('-width' => 320, '-height' => 200)
 
canvas.createLine(  0,  25, 320,  25, '-tags' => <plate>,     '-width' => 2, '-fill' => :grey50)
canvas.createOval(155,  20, 165,  30, '-tags' => <pivot outline>,            '-fill' => :grey50)
canvas.createLine(  1,   1,    1,  1, '-tags' => <rod width>, '-width' => 3, '-fill' => :black)
canvas.createOval(  1,   1,    2,  2, '-tags' => <bob outline>,              '-fill' => :yellow)
 
canvas.raise(:pivot)
canvas.pack('-fill' => :both, '-expand' => 1)
var(θ = 45, Δθ = 0, length = 150, homeX = 160, homeY = 25)
 
func show_pendulum() {
    var angle = θ.deg2rad
    var x = (homeX + length*sin(angle))
    var y = (homeY + length*cos(angle))
    canvas.coords(:rod, homeX,  homeY,  x,      y)
    canvas.coords(:bob, x - 15, y - 15, x + 15, y + 15)
}
 
func recompute_angle() {
    var scaling = 3000/(length**2)
 
    # first estimate
    var firstΔΔθ = (-sin(θ.deg2rad) * scaling)
    var midΔθ    = (Δθ + firstΔΔθ)
    var midθ     = ((Δθ + midΔθ)/2 + θ)
 
    # second estimate
    var midΔΔθ = (-sin(midθ.deg2rad) * scaling)
    midΔθ      = ((firstΔΔθ + midΔΔθ)/2 + Δθ)
    midθ       = ((Δθ + midΔθ)/2 + θ)
 
    # again, first
    midΔΔθ     = (-sin(midθ.deg2rad) * scaling)
    var lastΔθ = (midΔθ + midΔΔθ)
    var lastθ  = ((midΔθ + lastΔθ)/2 + midθ)
 
    # again, second
    var lastΔΔθ = (-sin(lastθ.deg2rad) * scaling)
    lastΔθ      = ((midΔΔθ + lastΔΔθ)/2 + midΔθ)
    lastθ       = ((midΔθ + lastΔθ)/2 + midθ)
 
    # Now put the values back in our globals
    Δθ = lastΔθ
    θ  = lastθ
}
 
func animate(Ref id) {
    recompute_angle()
    show_pendulum()
    *id = root.after(15 => { animate(id) })
}
 
show_pendulum()
var after_id = root.after(500 => { animate(\after_id) })
 
canvas.bind('<Destroy>' => { after_id.cancel })
%S<Tk>.MainLoop()
```
