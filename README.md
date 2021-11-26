# Hangman-Game
*/can you guess the correct word in order to save your fellow man from Abduction?*/
#include <iostream>
#include "ufo_functions.hpp"
using namespace std;
//     g++ ufo.cpp ufo_functions.cpp
int main() {
  greet();

  std::string codeword = "codecademy";
  std::string answer = "__________";
  int misses = 0;
  std::vector<char> incorrect;
  bool guess = false;
  char letter;

  while(answer != codeword && misses < 7) {
    display_misses(misses);
    display_status(incorrect,answer);
    cout << "\n\nPlease enter your guess: \n";
    cin >> letter;

    for(int i = 0; i < codeword.length(); i++) {
      if(letter == codeword[i]) {
        answer[i] = letter;
        guess = true;
      } 
    }
     if(guess) {
        cout << "\nCorrect\n";
      }
      else {
        cout << "\nIncorrect! The tractor beam pulls their victim in further!\n";
        incorrect.push_back(letter);
        misses++;
      }
  
  guess = false;
  }
  end_game(answer,codeword);
}
