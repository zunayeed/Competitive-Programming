# Special Srting again
  - [Special Sring again HackerRank](https://www.hackerrank.com/challenges/special-palindrome-again/copy-from/171893640?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=strings)
```java
static long substrCount(int n, String s) {
	    // initialize counter to n because each character is a
	    // palindromic string
	    int counter = n;
					
	    // to count consecutive characters that are the same
	    int consec = 1;
					
	    // the middle index of a 3-character symmetry,
	    // assigned only once detected
	    int midIndex = -1;
					
	    // compare with previous character so start with i=1
	    for (int i = 1; i < n; i++) {
	        if (s.charAt(i) == s.charAt(i-1)) {
	            // Condition 1: All of the characters are the same
	            // For n consecutive characters that are the same,
	            // we have this formula:
	            // Number of palindromic strings =
	            //     (n-1) + (n-2) + ... + (n-(n-1))
	            counter += consec;
	            consec++;
	                
	            // Condition 2: All characters except the middle one
	            // are the same
	            if (midIndex > 0) {
	                // check for symmetry on both sides
	                // of the midIndex
	                if ((midIndex-consec) > 0 && s.charAt(midIndex-consec) == s.charAt(i)) {
	                    counter++;
	                } else {
	                    // no more possibility of palindromic string
	                    // with this midIndex
	                    midIndex = -1; 
	                }
	            }
	        } else {
	            // reset consecutive chars counter to 1
	            consec = 1;
	                
	            // check for a 3-character symmetry
	            if (((i-2) >= 0) && s.charAt(i-2) == s.charAt(i)) {
	                counter++; // 3-char symmetry is detected
	                    
	                // to check if the next characters are the same
	                // and symmetrical along the midIndex
	                midIndex = i-1;
	            } else {
	                midIndex = -1;
	            }
	        }
	    }
	    return counter;
	}
  ```
  ------------------------------------------------------------------------------------------------------------
  ```java
  // Complete the substrCount function below.
    static long substrCount(int n, String s) {
        long retVal = n;
        for(int i=0; i<n;i++){
            int diffCharIndex = -1; 
            for(int j =i+1; j<n;j++){
                if(s.charAt(i)==s.charAt(j)){
                    if((diffCharIndex == -1)||((j-diffCharIndex)==(diffCharIndex-i))){
                        retVal++;
                    }
                }
                else{
                    if(diffCharIndex == -1){
                        diffCharIndex = j;}
                     else {
                     break;    
                    }
                }
            }
        }
        return retVal; 
    }
```
