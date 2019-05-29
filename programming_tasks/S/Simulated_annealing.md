[1]: https://rosettacode.org/wiki/Simulated_annealing

# [Simulated annealing][1]

```ruby
module TravelingSalesman {
 
    # Eₛ: length(path)
    func Eₛ(distances, path) {
        var total = 0
        [path, path.slice(1)].zip {|ci,cj|
            total += distances[ci-1][cj-1]
        }
        total
    }
 
    # T: temperature
    func T(k, kmax, kT) { kT * (1 - k/kmax) }
 
    # ΔE = Eₛ_new - Eₛ_old > 0
    # Prob. to move if ΔE > 0, → 0 when T → 0 (fronzen state)
    func P(ΔE, k, kmax, kT) { exp(-ΔE / T(k, kmax, kT)) }
 
    # ∆E from path ( .. a u b .. c v d ..) to (.. a v b ... c u d ..)
    # ∆E before swapping (u,v)
    # Quicker than Eₛ(s_next) - Eₛ(path)
    func dE(distances, path, u, v) {
 
        var a = distances[path[u-1]-1][path[u]-1]
        var b = distances[path[u+1]-1][path[u]-1]
        var c = distances[path[v-1]-1][path[v]-1]
        var d = distances[path[v+1]-1][path[v]-1]
 
        var na = distances[path[u-1]-1][path[v]-1]
        var nb = distances[path[u+1]-1][path[v]-1]
        var nc = distances[path[v-1]-1][path[u]-1]
        var nd = distances[path[v+1]-1][path[u]-1]
 
        if (v == u+1) {
            return ((na+nd) - (a+d))
        }
 
        if (u == v+1) {
            return ((nc+nb) - (c+b))
        }
 
        return ((na+nb+nc+nd) - (a+b+c+d))
    }
 
    const dirs = [1, -1, 10, -10, 9, 11, -11, -9]
 
    func _prettypath(path) {
        path.slices(10).map { .map{ "%3s" % _ }.join(', ') }.join("\n")
    }
 
    func findpath(distances, kmax, kT) {
 
        const n = distances.len
        const R = 2..n
 
        var path = [1, R.shuffle..., 1]
        var Emin = Eₛ(distances, path)
 
        printf("# Entropy(s₀) = s%10.2f\n", Emin)
        printf("# Random path:\n%s\n\n", _prettypath(path))
 
        for k in (1 .. kmax) {
 
            if (k % (kmax//10) == 0) {
                printf("k: %10d | T: %8.4f | Eₛ: %8.4f\n", k, T(k, kmax, kT), Eₛ(distances, path))
            }
 
            var u = R.rand
            var v = (path[u-1] + dirs.rand)
            v ~~ R || next
 
            var δE = dE(distances, path, u-1, v-1)
            if ((δE < 0) || (P(δE, k, kmax, kT) >= 1.rand)) {
                path.swap(u-1, v-1)
                Emin += δE
            }
        }
 
        printf("k: %10d | T: %8.4f | Eₛ: %8.4f\n", kmax, T(kmax, kmax, kT), Eₛ(distances, path))
        say ("\n# Found path:\n", _prettypath(path))
        return path
    }
}
 
var citydist = {|ci|
    { |cj|
        var v1 = Vec(ci%10, ci//10)
        var v2 = Vec(cj%10, cj//10)
        v1.dist(v2)
    }.map(1..100)
}.map(1..100)
 
TravelingSalesman::findpath(citydist, 1e6, 1)
```

#### Output:
```
# Entropy(s₀) =     520.29
# Random path:
  1,  10,  79,  52,  24,   9,  58,  11,  42,   4
 15,  87,  62,  88,  21,  91,  99,  84,  61,  14
  5,  17,  33,  95,  74,  31,  40,  13,  37,  69
  6,  22,  97,  45,  56,  63,  75,  83,  53,  41
  3,  47,  89,  80,  78,  98,  46,  18,  25,  51
 93,  16,  50,  30,  48,   8,  66,  68,  59,  73
 49,  96,  36,  32, 100,  27,  76,  44,  64,  39
 90,  82,  20,  12,  54,  86,  29,  81,  26,  72
 60,  94,  35,  92,  43,   7,  85,  55,  28,  57
 23,  34,  65,  71,  38,   2,  77,  70,  19,  67
  1

k:     100000 | T:   0.9000 | Eₛ: 185.1809
k:     200000 | T:   0.8000 | Eₛ: 168.6262
k:     300000 | T:   0.7000 | Eₛ: 146.5948
k:     400000 | T:   0.6000 | Eₛ: 140.1441
k:     500000 | T:   0.5000 | Eₛ: 129.5132
k:     600000 | T:   0.4000 | Eₛ: 132.8942
k:     700000 | T:   0.3000 | Eₛ: 124.2865
k:     800000 | T:   0.2000 | Eₛ: 120.0859
k:     900000 | T:   0.1000 | Eₛ: 115.0771
k:    1000000 | T:   0.0000 | Eₛ: 114.9728
k:    1000000 | T:   0.0000 | Eₛ: 114.9728

# Found path:
  1,   2,  13,   3,   4,   5,   6,   7,   8,   9
 19,  29,  18,  28,  27,  17,  16,  26,  25,  15
 14,  24,  23,  12,  11,  10,  20,  21,  30,  40
 41,  31,  32,  44,  45,  46,  47,  48,  49,  39
 38,  37,  36,  35,  34,  42,  51,  50,  60,  61
 52,  53,  54,  55,  56,  57,  58,  59,  69,  68
 77,  67,  66,  65,  64,  62,  72,  71,  70,  80
 81,  82,  74,  75,  76,  87,  88,  78,  79,  89
 99,  98,  97,  96,  86,  85,  83,  91,  90, 100
 92,  93,  94,  95,  84,  73,  63,  43,  33,  22
  1
```
