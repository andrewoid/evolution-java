### Counting Duplicates

What if instead you want to show the duplicates in an array AND count how many of each element exists.

    package [lastname].math;
    public class CountDuplicates {
    
        public static void main( String args[] ) {
    
            String array[] = new String[] {
                "A", "B", "B", "C"
            };
            
            ...
        
        }
    }
    
In this instance we need more than Set. We need a way to **Map** a String to it's corresponding count. If you want to map one object (key) to another object (vaue), there is a simple data structure for that called a HashMap. It is useful to take a look at the [Map](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) interface as well as the [HashMap](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html) class.

    package [lastname].math;
    public class CountDuplicates {
    
        public static void main( String args[] ) {
    
            String array[] = new String[] {
                "A", "B", "B", "C"
            };
            
            HashMap<String, Integer> map = new HashMap<String, Integer>();
            
            // fill the HashMap
            for ( String key : array ) {
                int value = map.get(key);
                if ( value == null ) {
                    map.put(key, 1);
                }
                else {
                    map.put(key, value+1);
                }
            }
            
            // iterate through the HashMap's key-value pairs
            for ( Map.Entry<String, Integer> entry : map.entrySet ) {
                System.out.println(entry.getKey() + " " + entry.getValue());
            }
        
        }
    }