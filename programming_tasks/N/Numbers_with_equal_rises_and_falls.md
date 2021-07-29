[1]: https://rosettacode.org/wiki/Numbers_with_equal_rises_and_falls

# [Numbers with equal rises and falls][1]

```ruby
func isok(arr) {
    var diffs = arr.map_cons(2, {|a,b| a - b })
    diffs.count { .is_pos } == diffs.count { .is_neg }
}
 
var base = 10
 
with (200) {|n|
    say "First #{n} terms (base #{base}):"
    n.by { isok(.digits(base)) && .is_pos }.each_slice(20, {|*a|
        say a.map { '%3s' % _ }.join(' ')
    })
}
 
with (1e7) {|n|     # takes a very long time
    say "\nThe #{n.commify}-th term (base #{base}): #{
            n.th { isok(.digits(base)) && .is_pos }.commify}"
}
```

#### Output:
```
First 200 terms (base 10):
  1   2   3   4   5   6   7   8   9  11  22  33  44  55  66  77  88  99 101 102
103 104 105 106 107 108 109 111 120 121 130 131 132 140 141 142 143 150 151 152
153 154 160 161 162 163 164 165 170 171 172 173 174 175 176 180 181 182 183 184
185 186 187 190 191 192 193 194 195 196 197 198 201 202 203 204 205 206 207 208
209 212 213 214 215 216 217 218 219 222 230 231 232 240 241 242 243 250 251 252
253 254 260 261 262 263 264 265 270 271 272 273 274 275 276 280 281 282 283 284
285 286 287 290 291 292 293 294 295 296 297 298 301 302 303 304 305 306 307 308
309 312 313 314 315 316 317 318 319 323 324 325 326 327 328 329 333 340 341 342
343 350 351 352 353 354 360 361 362 363 364 365 370 371 372 373 374 375 376 380
381 382 383 384 385 386 387 390 391 392 393 394 395 396 397 398 401 402 403 404

The 10,000,000-th term (base 10): 41,909,002
```
