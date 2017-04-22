[1]: http://rosettacode.org/wiki/Unicode_strings

# [Unicode strings][1]

Sidef uses UTF-8 encoding for pretty much everything, including source files, strings, stdout, stderr and stdin.

```ruby
# International class; name and street
 class 国際( なまえ, Straße ) {
 
    # Say who am I!
    method 言え {
        say "I am #{self.なまえ} from #{self.Straße}"
    }
}
 
 # all the people of the world!
 var 民族 = [
              国際( "高田　Friederich", "台湾" ),
              国際( "Smith Σωκράτης", "Cantù" ),
              国際( "Stanisław Lec", "południow" ),
           ]
 
民族.each { |garçon|
    garçon.言え
}
```

#### Output:
```
I am 高田　Friederich from 台湾
I am Smith Σωκράτης from Cantù
I am Stanisław Lec from południow
```
