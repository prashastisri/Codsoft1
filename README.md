package program1;

import java.util.Scanner;
import java.util.Random;
public class Codsoft1{
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int minRange = 1;
        int maxRange = 100;
        int maxAttempts = 10;
        int score = 0;
        
        System.out.println("Welcome to Guess the Number!");
        
        while (true) {
            int numberToGuess = random.nextInt(maxRange - minRange + 1) + minRange;
            int attempts = 0;
            boolean correctGuess = false;
            
            System.out.println("\nI've selected a number between " + minRange + " and " + maxRange + ".");
            System.out.println("You have " + maxAttempts + " attempts to guess it.");
            
            while (attempts < maxAttempts && !correctGuess) {
                System.out.print("Enter your guess: ");
                int guess = scanner.nextInt();
                attempts++;
                
                if (guess == numberToGuess) {
                    System.out.println("Congratulations! You've guessed the correct number in " + attempts + " attempts.");
                    correctGuess = true;
                    score++;
                } else if (guess < numberToGuess) {
                    System.out.println("Too low! Try again.");
                } else {
                    System.out.println("Too high! Try again.");
                }
            }
            
            if (!correctGuess) {
                System.out.println("Sorry, you've run out of attempts. The number was " + numberToGuess + ".");
            }
            
            System.out.println("\nYour current score: " + score);
            
            System.out.print("Do you want to play again? (yes/no): ");
            String playAgain = scanner.next().toLowerCase();
            
            if (!playAgain.equals("yes")) {
                break;
            }
        }
        
        System.out.println("\nThanks for playing Guess the Number!");
        scanner.close();
    }
}
