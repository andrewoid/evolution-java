##ScrabbleDictionary

You work for a company making a "Scrabble type" game. You must create a class called ScrabbleDictionary. You can download a dictionary text file from the [WinEdt website](http://www.winedt.org/Dict/). Download the English language zip file. Inside you will find a file called "US.dic".

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
    
Also create a ScrabbleDictionaryTest class that has methods to test the contains() and getWordsWith() methods. 

Make sure when you finish that you push the ScrabbleDictionary.java, ScrabbleDictionaryTest.java and US.dic files to github.