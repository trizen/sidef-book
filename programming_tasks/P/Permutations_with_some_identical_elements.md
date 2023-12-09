[1]: https://rosettacode.org/wiki/Permutations_with_some_identical_elements

# [Permutations with some identical elements][1]

Simple implementation, by filtering out the duplicated permutations.

```ruby
func permutations_with_some_identical_elements (reps) {
    reps.map_kv {|k,v| v.of(k+1)... }.permutations.uniq
}
 
say permutations_with_some_identical_elements([2,1]).map{.join}.join(' ')
say permutations_with_some_identical_elements([2,3,1]).map{.join}.join(' ')
```

#### Output:
```
112 121 211
112223 112232 112322 113222 121223 121232 121322 122123 122132 122213 122231 122312 122321 123122 123212 123221 131222 132122 132212 132221 211223 211232 211322 212123 212132 212213 212231 212312 212321 213122 213212 213221 221123 221132 221213 221231 221312 221321 222113 222131 222311 223112 223121 223211 231122 231212 231221 232112 232121 232211 311222 312122 312212 312221 321122 321212 321221 322112 322121 322211
```


More efficient approach, by generating the permutations without duplicates:

```ruby
func next_unique_perm (array) {

    var k = array.end
    return ([], false) if (k < 0)
    var i = k-1

    while ((i >= 0) && (array[i] >= array[i+1])) {
        --i
    }

    return (array.flip, false) if (i == -1)

    if (array[i+1] > array[k]) {
        array = [array.first(i+1)..., array.slice(i+1).first(k).flip...]
    }

    var j = i+1
    while (array[i] >= array[j]) {
        j++
    }

    array.clone!
    array.swap(i,j)

    return (array, true)
}

func unique_permutations(array) {
    var perm  = array
    var perms = [perm]
    loop {
        (perm, var more) = next_unique_perm(perm)
        break if !more
        perms << perm
    }
    return perms
}

for arr in ([[1,1,2], [1,1,2,2,2,3], %w(A A B B B C)]) {
    say "\nPermutations with array = #{arr}:"
    say unique_permutations(arr).map{.join}.join(' ')
}
```

#### Output:
```
Permutations with array = [1, 1, 2]:
112 121 211

Permutations with array = [1, 1, 2, 2, 2, 3]:
112223 112232 112322 113222 121223 121232 121322 122123 122132 122213 122231 122312 122321 123122 123212 123221 131222 132122 132212 132221 211223 211232 211322 212123 212132 212213 212231 212312 212321 213122 213212 213221 221123 221132 221213 221231 221312 221321 222113 222131 222311 223112 223121 223211 231122 231212 231221 232112 232121 232211 311222 312122 312212 312221 321122 321212 321221 322112 322121 322211

Permutations with array = ["A", "A", "B", "B", "B", "C"]:
AABBBC AABBCB AABCBB AACBBB ABABBC ABABCB ABACBB ABBABC ABBACB ABBBAC ABBBCA ABBCAB ABBCBA ABCABB ABCBAB ABCBBA ACABBB ACBABB ACBBAB ACBBBA BAABBC BAABCB BAACBB BABABC BABACB BABBAC BABBCA BABCAB BABCBA BACABB BACBAB BACBBA BBAABC BBAACB BBABAC BBABCA BBACAB BBACBA BBBAAC BBBACA BBBCAA BBCAAB BBCABA BBCBAA BCAABB BCABAB BCABBA BCBAAB BCBABA BCBBAA CAABBB CABABB CABBAB CABBBA CBAABB CBABAB CBABBA CBBAAB CBBABA CBBBAA
```
