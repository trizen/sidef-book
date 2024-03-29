[1]: https://rosettacode.org/wiki/Bitmap/Write_a_PPM_file

# [Bitmap/Write a PPM file][1]

```ruby
subset Int   < Number {|n| n.is_int  }
subset UInt  < Int    {|n| n >= 0    }
subset UInt8 < Int    {|n| n ~~ ^256 }

struct Pixel {
    R < UInt8,
    G < UInt8,
    B < UInt8
}

class Bitmap(width < UInt, height < UInt) {
    has data = []

    method fill(Pixel p) {
        data = (width*height -> of { Pixel(p.R, p.G, p.B) })
    }

    method setpixel(i < UInt, j < UInt, Pixel p) {

        subset WidthLimit  < UInt { |n| n ~~ ^width  }
        subset HeightLimit < UInt { |n| n ~~ ^height }

        func (w < WidthLimit, h < HeightLimit) {
            data[w*height + h] = p
        }(i, j)
    }

    method p6 {
        <<-EOT + data.map {|p| [p.R, p.G, p.B].pack('C3') }.join
        P6
        #{width} #{height}
        255
        EOT
    }
}

var b = Bitmap(width: 125, height: 125)

for i,j in (^b.height ~X ^b.width) {
    b.setpixel(i, j, Pixel(2*i, 2*j, 255 - 2*i))
}

%f"palette.ppm".write(b.p6, :raw)
```
