# Unordered List

All CRUD operation time is ==O(1)==

## HashSet

```java
HashSet<Integer> set = new HashSet<>();

set.add(3); // add a value
set.remove(3); // remove this value in this set
```



## HashMap



```java
HashMap<Integer, String> map = new HashMap();



map.put(1, "a"); // add a pair to map
map.put(1, "b"); // update the map

map.get(1); // get value of key 1

map.containsKey(1); // return T/F
```



# Odered List

All CRUD operation time is ==O(long)==

By default, TreeMap TreeSet sort all its entries according to their natural ordering. For an integer, this would mean ascending order and for strings, alphabetical order.

## TreeSet

```java
TreeSet<Integer> set = new TreeSet<>();

set.add(3); // add a value
set.remove(3); // remove this value in this set
```



## TreeMap

![orderedList](/Users/blake/Desktop/JavaNotes/Java/pictures/orderedList.png)



