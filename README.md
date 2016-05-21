package com.dimitrisli.springJdbcOracle.testsql;

import java.util.*;
import java.io.*;

class Main {
  public static String LongestWord(String sen) {

    // code goes here
    /*
     * Note: In Java the return type of a function and the parameter types being passed are defined,
     * so this return call must match the return type of the function. You are free to modify the
     * return type.
     */
    int maxLength = 0;
    int curWordLength = 0;
    int curPuncLen = 0; // maintian this to return wors with punctuations
    String longestWord = "";
    char[] senArr = sen.toCharArray();
    for (int i = 0; i < senArr.length; i++) {
      if (!isPunctuation(senArr[i]) && senArr[i] != ' ') { // not a punctuation and not space
                                                           // increase length
        curWordLength++;
      }
      if (isPunctuation(senArr[i])) {
        curPuncLen++;
      }
      if (senArr[i] == ' ' || (i== (sen.length()-1)) ) { // space or the index of the last character, can be the stopp
        if (curWordLength > maxLength) {
          // reset the fields
          maxLength = curWordLength;
          longestWord = sen.substring(i - ((curWordLength + curPuncLen)), i);
          curWordLength = 0;
          curPuncLen = 0;
        } else { // reset the counters even if the stop conditions are not reached
          curWordLength = 0;
          curPuncLen = 0;
        }
      }

    }


    return longestWord;

  }

  private static boolean isPunctuation(char c) {
    return c == ',' || c == '.' || c == '!' || c == '?' || c == ':' || c == ';';
  }

  public static void main(String[] args) {
    // keep this function call here
    Scanner s = new Scanner(System.in);
    System.out.print(LongestWord(s.nextLine()));
  }

}
