[1]: https://rosettacode.org/wiki/Audio_frequency_generator

# [Audio frequency generator][1]

```ruby
var (kindS = 'sine', kind = 0, freq = 0, vol = 0, dur = 0)

while ((freq < 40) || (freq > 10000)) {
    freq = (Sys.read("Enter frequency in Hz (40 to 10000) : ", Num) || next)
}

while ((vol < 1) || (vol > 50)) {
    vol = (Sys.read("Enter volume in dB (1 to 50) : ", Num) || next)
}

while ((dur < 2) || (dur > 10)) {
    dur = (Sys.read("Enter duration in seconds (2 to 10) : ", Num) || next)
}

while ((kind < 1) || (kind > 3)) {
    kind = (Sys.read("Enter kind (1 = Sine, 2 = Square, 3 = Sawtooth) : ", Num) || next)

    given(kind) {
        when (1) { kindS = 'sine' }
        when (2) { kindS = 'square' }
        when (3) { kindS = 'sawtooth' }
    }
}

var args = ["-n", "synth", dur, kindS, freq, "vol", vol, "dB"]
Sys.run('play', args...)
```
