[1]: https://rosettacode.org/wiki/Percentage_difference_between_images

# [Percentage difference between images][1]

```ruby
require('Imager')
 
func img_diff(a, b) {
 
    func from_file(name) {
         %O<Imager>.new(file => name)
    }
 
    func size(img) {
        (img.getwidth, img.getheight)
    }
 
    func pixel_diff(p1, p2) {
        [p1.rgba] »-« [p2.rgba] -> map { .abs }.sum
    }
 
    func read_pixel(img, x, y) {
        img.getpixel(x => x, y => y)
    }
 
    var(img1, img2) = (from_file(a), from_file(b))
 
    var(w1, h1) = size(img1)
    var(w2, h2) = size(img2)
 
    if ((w1 != w2) || (h1 != h2)) {
        return nil
    }
 
    var sum = 0
    for y=(^h1), x=(^w1) {
        sum += pixel_diff(read_pixel(img1, x, y), read_pixel(img2, x, y))
    }
 
    sum / (w1 * h1 * 255 * 3)
}
 
say 100*img_diff('Lenna50.jpg', 'Lenna100.jpg')
```

#### Output:
```
1.62559309816048815359477124183007
```
