[1]: https://rosettacode.org/wiki/MD5/Implementation

# [MD5/Implementation][1]

```ruby
class MD5(String msg) {

    method init {
        msg = msg.bytes
    }

    const FGHI = [
        {|a,b,c| (a & b) | (~a & c) },
        {|a,b,c| (a & c) | (b & ~c) },
        {|a,b,c| (a ^ b ^ c)        },
        {|a,b,c| (b ^ (a | ~c))     },
    ]

    const S = [
        [7, 12, 17, 22] * 4,
        [5,  9, 14, 20] * 4,
        [4, 11, 16, 23] * 4,
        [6, 10, 15, 21] * 4,
    ].flat

    const T = 64.of {|i| floor(abs(sin(i+1)) * 1<<32) }

    const K = [
        ^16 -> map {|n|    n           },
        ^16 -> map {|n| (5*n + 1) % 16 },
        ^16 -> map {|n| (3*n + 5) % 16 },
        ^16 -> map {|n| (7*n    ) % 16 },
    ].flat

    func radix(Number b, Array a) {
        ^a -> sum {|i| b**i * a[i] }
    }

    func little_endian(Number w, Number n, Array v) {
        var step1 = (^n »*» w)
        var step2 = (v ~X>> step1)
        step2 »%» (1 << w)
    }

    func block(Number a, Number b) { (a  + b) & 0xffffffff }
    func srble(Number a, Number n) { (a << n) & 0xffffffff | (a >> (32-n)) }

    func md5_pad(msg) {
        var bits = 8*msg.len
        var padded = [msg..., 128, [0] * (-(floor(bits / 8) + 1 + 8) % 64)].flat

        gather {
            padded.each_slice(4, {|*a|
                take(radix(256, a))
            })
            take(little_endian(32, 2, [bits]))
        }.flat
    }

    func md5_block(Array H, Array X) {
        var (A, B, C, D) = H...

        for i in ^64 {
            (A, B, C, D) = (D,
                block(B, srble(
                    block(
                        block(
                            block(A, FGHI[floor(i / 16)](B, C, D)), T[i]
                        ), X[K[i]]
                    ), S[i])
                ), B, C)
        }

        for k,v in ([A, B, C, D].kv) {
            H[k] = block(H[k], v)
        }

        return H
    }

    method md5_hex {
        self.md5.map {|n| '%02x' % n }.join
    }

    method md5 {
        var M = md5_pad(msg)
        var H = [0x67452301, 0xefcdab89, 0x98badcfe, 0x10325476]

        for i in (range(0, M.end, 16)) {
            md5_block(H, M.slice(i).first(16))
        }

        little_endian(8, 4, H)
    }
}

var tests = [
    ['d41d8cd98f00b204e9800998ecf8427e', ''],
    ['0cc175b9c0f1b6a831c399e269772661', 'a'],
    ['900150983cd24fb0d6963f7d28e17f72', 'abc'],
    ['f96b697d7cb7938d525a2f31aaf161d0', 'message digest'],
    ['c3fcd3d76192e4007dfb496cca67e13b', 'abcdefghijklmnopqrstuvwxyz'],
    ['d174ab98d277d9f5a5611c2c9f419d9f', 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789'],
    ['57edf4a22be3c955ac49da2e2107b67a', '12345678901234567890123456789012345678901234567890123456789012345678901234567890'],
]

for md5,msg in tests {
    var hash = MD5(msg).md5_hex
    say "#{hash} : #{msg}"

    if (hash != md5) {
        say "\tHowever, that is incorrect (expected: #{md5})"
    }
}
```

#### Output:
```
d41d8cd98f00b204e9800998ecf8427e :
0cc175b9c0f1b6a831c399e269772661 : a
900150983cd24fb0d6963f7d28e17f72 : abc
f96b697d7cb7938d525a2f31aaf161d0 : message digest
c3fcd3d76192e4007dfb496cca67e13b : abcdefghijklmnopqrstuvwxyz
d174ab98d277d9f5a5611c2c9f419d9f : ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789
57edf4a22be3c955ac49da2e2107b67a : 12345678901234567890123456789012345678901234567890123456789012345678901234567890
```
