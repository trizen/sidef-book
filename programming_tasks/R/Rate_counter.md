[1]: https://rosettacode.org/wiki/Rate_counter

# [Rate counter][1]

```ruby
var benchmark = frequire('Benchmark')
 
func job1 {
    #...job1 code...
}
func job2 {
    #...job2 code...
}
 
const COUNT = -1   # run for one CPU second
benchmark.timethese(COUNT, Hash('Job1' => job1, 'Job2' => job2))
```
