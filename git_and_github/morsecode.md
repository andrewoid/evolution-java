##MorseCode

Morse Code is a way of encoding a message so it can be transmitted over a wire easily. It was originally developed in the 1800s but is still in use today. Each letter, number of punctuation is encoded into a string of periods or dashes. 

For instance the letter "A" is encoded as ".-", "B" is encoded as "-..."

Refer to the table in the [Morse Code wikipedia page](https://en.wikipedia.org/wiki/Morse_code) for a full list of conversions.

Between each letter should be a space. So the string "ABC" should encode to ".- -... -.-."

Between each word should be three spaces "   "

    package [lastname].morsecode;

    public class MorseCode {
    
        public MorseCode() {
            ...
        }
        
        public String encode( String message ) {
            ...
        }
        
        public String decode( String code ) {
            ...
        }
    
    }

Also create a MorseCodeTest class that tests the encode() and decode() methods.