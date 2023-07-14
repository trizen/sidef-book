[1]: https://rosettacode.org/wiki/Fast_Fourier_transform

# [Fast Fourier transform][1]

```ruby
func fft(arr) {
    arr.len == 1 && return arr

    var evn = fft([arr[^arr -> grep { .is_even }]])
    var odd = fft([arr[^arr -> grep { .is_odd  }]])
    var twd = (Num.tau.i / arr.len)

    ^odd -> map {|n| odd[n] *= exp(twd * n) }
    (evn »+« odd) + (evn »-« odd)
}

var cycles = 3
var sequence = 0..15
var wave = sequence.map {|n| sin(n * Num.tau / sequence.len * cycles) }
say "wave:#{wave.map{|w| '%6.3f' % w }.join(' ')}"
say "fft: #{fft(wave).map { '%6.3f' % .abs }.join(' ')}"
```

#### Output:
```
wave: 0.000  0.924  0.707 -0.383 -1.000 -0.383  0.707  0.924  0.000 -0.924 -0.707  0.383  1.000  0.383 -0.707 -0.924
fft:  0.000  0.000  0.000  8.000  0.000  0.000  0.000  0.000  0.000  0.000  0.000  0.000  0.000  8.000  0.000  0.000
```
