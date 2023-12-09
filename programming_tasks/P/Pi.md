[1]: https://rosettacode.org/wiki/Pi

# [Pi][1]

### Classical Algorithm

```ruby
func pi(callback) {
    var (q, r, t, k, n, l) = (1, 0, 1, 1, 3, 3)
    loop {
        if ((4*q + r - t) < n*t) {
            callback(n)
            static _dot = callback('.')
            var nr = 10*(r - n*t)
            n = ((10*(3*q + r)) // t - 10*n)
            q *= 10
            r = nr
        }
        else {
            var nr = ((2*q + r) * l)
            var nn = ((q*(7*k + 2) + r*l) // (t*l))
            q *= k
            t *= l
            l += 2
            k += 1
            n = nn
            r = nr
        }
    }
}

STDOUT.autoflush(true)
pi(func(digit){ print digit })
```


### Quicker, Unverified Algorithm

From the same .pdf mentioned throughout this task, from the last page. The original algorithm was written in Haskell, this is a translation which has also been optimized to avoid redundant multiplications. Same output, but the algorithm is based on one of Gosper’s series that yields more than one digit per term on average, so no test is made partway through the iteration. This is capable of producing approximately 100,000 digits at [tio.run](https://tio.run/##Hc@9boNAEATg3k@xnXfvNjaXcEkUa7v0KeLU0fkwP7Zl4DgiIYtnJ4A0xTTfSNNV2Tmfpry/e2jQEzzgzwVsOXDkgi9c8pUdn3ggEEDD5j3h1zU2ZZOssfxCG4BbXTez9zgItgqdluc3Am1VoP3eqkgH6KKLlYffecvjdrddGEAQkygstFy02JTUok9znXGAp2GVrZJSy1VLmhwgKilghHHzffz8@jnuXB/r/NZ3JRr6aHB5gxk9mlDdI2QjTdM/) in the maximum 60 seconds allowed.

```ruby
func p(c) { var(q,r,t,g,j,h,k,a,b,y) = (1,180,60,60,54,10,10,15,3)
  loop { c(y=(q*(a+=27) +5*r)//5*t); static _ = c('.')
    r=10*(g+=j+=54)*(q*(b+=5) +r -y*t); q*=h+=k+=40; t*=g } }
p(func(d){print d})
```
