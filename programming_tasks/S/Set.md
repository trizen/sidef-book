[1]: http://rosettacode.org/wiki/Set

# [Set][1]

```ruby
class Set(*set) {
 
    method init {
        var elems = set;
        set = Hash.new;
        elems.each { |e| self += e }
    }
 
    method +(elem) {
        set{elem} = elem;
        self;
    }
 
    method del(elem) {
        set.delete(elem);
    }
 
    method has(elem) {
        set.has_key(elem);
    }
 
    method ∪(Set that) {
        Set(set.values..., that.values...);
    }
 
    method ∩(Set that) {
        Set(set.keys.grep{ |k| k ∈ that }
                    .map { |k| set{k} }...);
    }
 
    method ∖(Set that) {
        Set(set.keys.grep{|k| !(k ∈ that) }
                    .map {|k| set{k} }...);
    }
 
    method ^(Set that) {
        var d = ((self ∖ that) ∪ (that ∖ self));
        Set(d.values...);
    }
 
    method count { set.len }
 
    method ≡(Set that) {
        (self ∖ that -> count.is_zero) && (that ∖ self -> count.is_zero);
    }
 
    method values { set.values }
 
    method ⊆(Set that) {
        that.set.keys.each { |k|
            k ∈ self || return false;
        }
        return true;
    }
 
    method to_s {
        "Set{" + set.values.map{|e| "#{e}"}.sort.join(', ') + "}"
    }
}
 
class Object {
    method ∈(Set set) {
        set.has(self);
    }
}
```


Usage example:

```ruby
var x = Set(1, 2, 3);
5..7 -> each { |i| x += i };
 
var y = Set(1, 2, 4, x);
 
say "set x is: #{x}";
say "set y is: #{y}";
 
[1,2,3,4,x].each { |elem|
    say ("#{elem} is ", elem ∈ y ? '' : 'not', " in y");
}
 
var (w, z);
say ("union: ", x ∪ y);
say ("intersect: ", x ∩ y);
say ("z = x ∖ y = ", z = (x ∖ y) );
say ("y is ", x ⊆ y ? "" : "not ", "a subset of x");
say ("z is ", x ⊆ z ? "" : "not ", "a subset of x");
say ("z = (x ∪ y) ∖ (x ∩ y) = ", z = ((x ∪ y) ∖ (x ∩ y)));
say ("w = x ^ y = ", w = (x ^ y));
say ("w is ", w ≡ z ? "" : "not ", "equal to z");
say ("w is ", w ≡ x ? "" : "not ", "equal to x");
```

#### Output:
```
set x is: Set{1, 2, 3, 5, 6, 7}
set y is: Set{1, 2, 4, Set{1, 2, 3, 5, 6, 7}}
1 is  in y
2 is  in y
3 is not in y
4 is  in y
Set{1, 2, 3, 5, 6, 7} is  in y
union: Set{1, 2, 3, 4, 5, 6, 7, Set{1, 2, 3, 5, 6, 7}}
intersect: Set{1, 2}
z = x ∖ y = Set{3, 5, 6, 7}
y is not a subset of x
z is a subset of x
z = (x ∪ y) ∖ (x ∩ y) = Set{3, 4, 5, 6, 7, Set{1, 2, 3, 5, 6, 7}}
w = x ^ y = Set{3, 4, 5, 6, 7, Set{1, 2, 3, 5, 6, 7}}
w is equal to z
w is not equal to x
```