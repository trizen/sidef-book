[1]: http://rosettacode.org/wiki/Fast_Fourier_transform

# [Fast Fourier transform][1]

```ruby
func fft(arr) {
    arr.len == 1 && return arr;

    var evn = fft([arr.@[arr.range.grep { .is_even }]]);
    var odd = fft([arr.@[arr.range.grep { .is_odd  }]]);
    var twd = (Complex(0, Number.tau) / arr.len);

    odd.range.map {|n| odd[n] *= exp(twd * n)};
    (evn »+« odd) + (evn »-« odd);
}

var cycles = 3;
var sequence = 0..15;
var wave = sequence.map {|n| Complex(sin(n * Number.tau / sequence.len * cycles)) };
say "wave:#{wave.map{|w| '%6.3f' % w }}";
say "fft: #{fft(wave).map { '%6.3f' % .abs }}";
```

#### Output:
```
wave: 0.000  0.924  0.707 -0.383 -1.000 -0.383  0.707  0.924  0.000 -0.924 -0.707  0.383  1.000  0.383 -0.707 -0.924
fft:  0.000  0.000  0.000  8.000  0.000  0.000  0.000  0.000  0.000  0.000  0.000  0.000  0.000  8.000  0.000  0.000
```
