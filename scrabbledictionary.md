##ScrabbleDictionary

You work for a company making a "Scrabble type" game. You must create a class called ScrabbleDictionary.

    public class ScrabbleDictionary {
    
        public ScrabbleDictionary() {
            ...
        }
    
        /**
         * @return true if the dictionary contains the word, otherwise false. 
         */
        public boolean contains( String word ) {
            ...
        }
        
        /**
         * @return an ArrayList of words in the dictionary that match the letters or an empty ArrayList if there are no matching words.
         */
        public ArrayList<String> getWordsWith( String letters ) {
            ...
        }
    
    }