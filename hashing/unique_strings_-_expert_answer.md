###Unique Strings - Expert Answer

The expert answer uses a HashSet object. A "Set" is a ["A collection that contains no duplicate elements"](http://docs.oracle.com/javase/7/docs/api/java/util/Set.html). A HashSet is more efficient at adding/removing and looking up elements than an array or ArrayList and produces a lot cleaner code.

    package [lastname].math;
    public class UniqueStrings {
    
        public static void main( String args[] ) {
    
            String array[] = new String[] {
                "A", "B", "B", "C"
            };
            
            HashSet set = new HashSet<String>();
            for ( String s : array ) {
                if ( !set.contains(s) ) {
                    System.out.println(s);
                }
                set.add(s);
            }
            
        
        }
    }
    
    