[1]: https://rosettacode.org/wiki/Compare_sorting_algorithms%27_performance

# [Compare sorting algorithms&#039; performance][1]

*Array#sort* is a built-in method.

```ruby
class Array {
    method radix_sort(base=10) {
        var rounds = ([self.minmax].map{.abs}.max.ilog(base) + 1)
        for i in (0..rounds) {
            var buckets = (2*base -> of {[]})
            var base_i = base**i
            for n in self {
                var digit = idiv(n, base_i)%base
                digit += base if (0 <= n)
                buckets[digit].append(n)
            }
            self = buckets.flat
        }
        return self
    }

    func merge(left, right) {
        var result = []
        while (left && right) {
            result << [right,left].min_by{.first}.shift
        }
        result + left + right
    }

    method merge_sort {
        var len = self.len
        len < 2 && return self

        var (left, right) = self.part(len>>1)

        left  = left.merge_sort
        right = right.merge_sort

        merge(left, right)
    }

    method quick_sort {
        self.len < 2 && return self
        var p = self.rand          # to avoid the worst cases
        var g = self.group_by {|x| x <=> p }
        (g{-1} \\ []).quick_sort + (g{0} \\ []) + (g{1} \\ []).quick_sort
    }

    method shell_sort {
        var h = self.len
        while (h >>= 1) {
            range(h, self.end).each { |i|
                var k = self[i]
                var j
                for (j = i; (j >= h) && (k < self[j - h]); j -= h) {
                    self[j] = self[j - h]
                }
                self[j] = k
            }
        }
        return self
    }

    method insertion_sort {
        { |i|
            var j = i
            var k = self[i+1]
            while ((j >= 0) && (k < self[j])) {
                self[j+1] = self[j]
                j--
            }
            self[j+1] = k
        } * self.end
        return self
    }

    method bubble_sort {
        loop {
            var swapped = false
            { |i|
                if (self[i] > self[i+1]) {
                    self[i, i+1] = self[i+1, i]
                    swapped = true
                }
            } << ^self.end
            swapped || break
        }
        return self
    }
}

var data_size = [1e2, 1e3, 1e4, 1e5]
var data = []
data_size.each {|size|
    var ary = @(1..size)
    data << [size.of(1), ary, ary.shuffle, ary.reverse]
}

data = data.transpose

var  data_type = ["set to all ones", "ascending sequence",
                  "randomly shuffled", "descending sequence"]
print("Array size:          ")
say data_size.map{|size| "%9d" % size}.join

data.each_kv {|i, arys|
    say "\nData #{data_type[i]}:"
    [:sort, :radix_sort, :quick_sort, :merge_sort,
     :shell_sort, :insertion_sort, :bubble_sort].each {|m|
        printf("%20s ", m)
        var timeout = false
        arys.each {|ary|
            if (!timeout) {
                var t0 = Time.micro
                ary.clone.(m)
                printf("  %7.3f", (var t1 = (Time.micro - t0)))
                timeout = true if (t1 > 1.5)
            }
            else {
                print("   --.---")
            }
        }
        say ''
    }
}
```

#### Output:
```
Array size:                100     1000    10000   100000

Data set to all ones:
                sort     0.000    0.001    0.011    0.104
          radix_sort     0.003    0.026    0.249    2.957
          quick_sort     0.004    0.003    0.029    0.298
          merge_sort     0.009    0.112    1.269   17.426
          shell_sort     0.006    0.164    2.092   --.---
      insertion_sort     0.002    0.016    0.149    1.261
         bubble_sort     0.001    0.007    0.064    0.647

Data ascending sequence:
                sort     0.000    0.001    0.011    0.109
          radix_sort     0.006    0.063    0.739    9.657
          quick_sort     0.006    0.080    0.865    9.578
          merge_sort     0.008    0.102    1.178   14.079
          shell_sort     0.006    0.091    1.441   16.398
      insertion_sort     0.001    0.012    0.124    1.258
         bubble_sort     0.001    0.006    0.063    0.628

Data randomly shuffled:
                sort     0.001    0.009    0.126    1.632
          radix_sort     0.006    0.060    0.731    8.768
          quick_sort     0.005    0.058    0.742    9.516
          merge_sort     0.010    0.132    1.639   --.---
          shell_sort     0.010    0.167    2.931   --.---
      insertion_sort     0.019    1.989   --.---   --.---
         bubble_sort     0.069    7.333   --.---   --.---

Data descending sequence:
                sort     0.000    0.001    0.012    0.129
          radix_sort     0.006    0.061    0.732    8.926
          quick_sort     0.005    0.061    0.720    8.712
          merge_sort     0.008    0.097    1.148   13.456
          shell_sort     0.008    0.133    1.910   --.---
      insertion_sort     0.040    3.884   --.---   --.---
         bubble_sort     0.092    8.819   --.---   --.---
```
