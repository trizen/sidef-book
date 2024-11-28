[1]: https://rosettacode.org/wiki/CRC-32

# [CRC-32][1]

```ruby
func create_crc32_table {
    256.of {|k|
        8.times {
            if (k & 1) {
                k >>= 1
                k ^= 0xedb88320
            }
            else {
                k >>= 1
            }
        }
        k
    }
}

func crc32(str, crc = 0) {
    static crc_table = create_crc32_table()
    crc &= 0xffffffff
    crc ^= 0xffffffff
    str.codes.each {|c|
        crc = ((crc >> 8) ^ crc_table[(crc & 0xff) ^ c])
    }
    return ((crc & 0xffffffff) ^ 0xffffffff)
}

say crc32("The quick brown fox jumps over the lazy dog").as_hex
say crc32("over the lazy dog", crc32("The quick brown fox jumps ")).as_hex
```

#### Output:
```
414fa339
414fa339
```