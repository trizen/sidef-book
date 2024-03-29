[1]: https://rosettacode.org/wiki/K-d_tree

# [K-d tree][1]

```ruby
struct Kd_node {
    d,
    split,
    left,
    right,
}
 
struct Orthotope {
    min,
    max,
}
 
class Kd_tree(n, bounds) {
 
    method init {
        n = self.nk2(0, n);
    }
 
    method nk2(split, e) {
        return(nil) if (e.len <= 0);
        var exset = e.sort_by { _[split] }
        var m = (exset.len // 2);
        var d = exset[m];
        while ((m+1 < exset.len) && (exset[m+1][split] == d[split])) {
            ++m;
        }
 
        var s2 = ((split + 1) % d.len);     # cycle coordinates
        Kd_node(d: d, split: split,
                left:  self.nk2(s2, exset.first(m)),
                right: self.nk2(s2, exset.last(m-1)));
    }
}
 
struct T3 {
    nearest,
    dist_sqd = Inf,
    nodes_visited = 0,
}
 
func find_nearest(k, t, p) {
    func nn(kd, target, hr, max_dist_sqd) {
        kd || return T3(nearest: [0]*k);
 
        var nodes_visited = 1;
        var s = kd.split;
        var pivot = kd.d;
        var left_hr = Orthotope(hr.min, hr.max);
        var right_hr = Orthotope(hr.min, hr.max);
        left_hr.max[s] = pivot[s];
        right_hr.min[s] = pivot[s];
 
        var nearer_kd;
        var further_kd;
        var nearer_hr;
        var further_hr;
        if (target[s] <= pivot[s]) {
            (nearer_kd, nearer_hr) = (kd.left, left_hr);
            (further_kd, further_hr) = (kd.right, right_hr);
        }
        else {
            (nearer_kd, nearer_hr) = (kd.right, right_hr);
            (further_kd, further_hr) = (kd.left, left_hr);
        }
 
        var n1 = nn(nearer_kd, target, nearer_hr, max_dist_sqd);
        var nearest = n1.nearest;
        var dist_sqd = n1.dist_sqd;
        nodes_visited += n1.nodes_visited;
 
        if (dist_sqd < max_dist_sqd) {
            max_dist_sqd = dist_sqd;
        }
        var d = (pivot[s] - target[s] -> sqr);
        if (d > max_dist_sqd) {
            return T3(nearest: nearest, dist_sqd: dist_sqd, nodes_visited: nodes_visited);
        }
        d = (pivot ~Z- target »sqr»() «+»);
        if (d < dist_sqd) {
            nearest = pivot;
            dist_sqd = d;
            max_dist_sqd = dist_sqd;
        }
 
        var n2 = nn(further_kd, target, further_hr, max_dist_sqd);
        nodes_visited += n2.nodes_visited;
        if (n2.dist_sqd < dist_sqd) {
            nearest = n2.nearest;
            dist_sqd = n2.dist_sqd;
        }
 
        T3(nearest: nearest, dist_sqd: dist_sqd, nodes_visited: nodes_visited);
    }
 
    return nn(t.n, p, t.bounds, Inf);
}
 
func show_nearest(k, heading, kd, p) {
    print <<-"END"
        #{heading}:
        Point:            [#{p.join(',')}]
        END
    var n = find_nearest(k, kd, p);
    print <<-"END"
        Nearest neighbor: [#{n.nearest.join(',')}]
        Distance:         #{sqrt(n.dist_sqd)}
        Nodes visited:    #{n.nodes_visited()}
 
        END
}
 
func random_point(k) { k.of { 1.rand } }
func random_points(k, n) { n.of { random_point(k) } }
 
var kd1 = Kd_tree([[2, 3],[5, 4],[9, 6],[4, 7],[8, 1],[7, 2]],
              Orthotope(min: [0, 0], max: [10, 10]));
show_nearest(2, "Wikipedia example data", kd1, [9, 2]);
 
var N = 1000
var t0 = Time.micro
var kd2 = Kd_tree(random_points(3, N), Orthotope(min: [0,0,0], max: [1,1,1]))
 
var t1 = Time.micro
show_nearest(2,
    "k-d tree with #{N} random 3D points (generation time: #{t1 - t0}s)",
     kd2, random_point(3))
```

#### Output:
```
Wikipedia example data:
Point:            [9,2]
Nearest neighbor: [8,1]
Distance:         1.41421356237309504880168872420969807856967187537695
Nodes visited:    3

k-d tree with 1000 random 3D points (generation time: 0.25858s):
Point:            [0.28961099389483532140941908632585463245703951185091,0.53383735570157521548169561846919925542828568155241,0.06543742264584889854604603500785549847809104064543]
Nearest neighbor: [0.28344130897803248636407083474733485442276225490765,0.54224255944924304382130637584184680424540291089424,0.12494797195998536910186918458377312162395340543897]
Distance:         0.06041703353924870133411659885818573345011076349573
Nodes visited:    30
```
