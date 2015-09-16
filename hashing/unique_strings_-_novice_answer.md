###Unique Strings - Novice Answer

    package [lastname].math;
    public class UniqueStrings {
    
        public static void main( String args[] ) {
    
            String array[] = new String[] {
                "A", "B", "B", "C"
            };
            
            for ( int i=0; i<array.length; i++ ) {
                boolean found = false;
                for ( int j=0; j<i; j++ ) {
                    if ( array[i].equals(array[j]) ) {
                         found = true;
                    }
                }
                if ( !found ) {
                    System.out.println(array[i]);
                }
            }
            
        
        }
    }
    
The novice answer above is to simply compare every element in the array to the one before it. If it exists in the array then it's a duplicate and it should not be printed.

The problem with this answer is not that it is the wrong answer, it is that it's inefficient. For a very large array (millions of elements) you would need to check millions of elements for each element in the array. 