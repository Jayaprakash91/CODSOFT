import java.util.Random;
import java.util.Scanner;


public class NumberGuessGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int minRange = 1;
        int maxRange = 100;
        int maxAttempts = 10;
        int score = 0;

        System.out.println("Welcome to the Number Guessing Game!");
        System.out.println("I'm thinking of a number between " + minRange + " and " + maxRange);

        boolean playAgain = true;
        while (playAgain) {
            int generatedNumber = random.nextInt(maxRange - minRange + 1) + minRange;
            System.out.println("New round! Guess the number. You have " + maxAttempts + " attempts.");

            int attempts = 0;
            boolean guessedCorrectly = false;

            while (attempts < maxAttempts && !guessedCorrectly) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                scanner.nextLine(); // Consume newline left from nextInt()

                attempts++;

                if (userGuess == generatedNumber) {
                    System.out.println("Congratulations! You've guessed the number " + generatedNumber + " correctly!");
                    guessedCorrectly = true;
                    score++;
                } else if (userGuess < generatedNumber) {
                    System.out.println("Too low! Try again.");
                } else {
                    System.out.println("Too high! Try again.");
                }
            }

            if (!guessedCorrectly) {
                System.out.println("Sorry, you've run out of attempts. The correct number was: " + generatedNumber);
            }

            System.out.print("Your score: " + score + " | Play again? (yes/no): ");
            String playChoice = scanner.nextLine().toLowerCase();

            if (!playChoice.equals("yes")) {
                playAgain = false;
            }
        }

        System.out.println("Thank you for playing the Number Guessing Game!");
        scanner.close();
    }
}

