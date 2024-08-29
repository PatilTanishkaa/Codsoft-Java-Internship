# Codsoft-Java-Internship-Task 1
import java.util.Random;
import java.util.Scanner;
public class GuessTheNumberGame {
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int minNum = 1;
        int maxNum = 100;
        int NoofAttempts = 10;
        int score = 0;
        int numberofrounds = 0;
        boolean playAgain = true;
        System.out.println(" ");
        System.out.println("Welcome to the Number Guessing Game!");

        while (playAgain) {
            int randomnumber = random.nextInt(maxNum - minNum+ 1) + minNum;
            int attempts = 0;
            numberofrounds++;
            
            System.out.println("\nRound " + numberofrounds + ":");
            
            while (attempts < NoofAttempts) {
                System.out.print("Guess the number between " + minNum+ " and " + maxNum+ ": ");
                
                while (!scanner.hasNextInt()) {
                    System.out.println("Invalid input. Please enter a valid number.");
                    scanner.next(); // Clear the invalid input
                }
                
                int guess = scanner.nextInt();
                attempts++;

                if (guess < minNum || guess > maxNum) {
                    System.out.println("Please enter a number within the range " + minNum+ " to " + maxNum+ ".");
                    continue;
                }

                if (guess == randomnumber){
                    System.out.println("Congratulations! You guessed the correct number " + randomnumber+ " in " + attempts + " attempts.");
                    score += NoofAttempts - attempts + 1; // Higher score for fewer attempts
                    break;
                } else if (guess < randomnumber) {
                    System.out.println("Too low! Try again.");
                } else {
                    System.out.println("Too high! Try again.");
                }
            }

            if (attempts == NoofAttempts) {
                System.out.println("Out of attempts! The correct number was " + randomnumber + ".");
            }

            System.out.println("Your current score is: " + score);
            System.out.print("Do you want to play another round? (yes/no): ");
            
            String response = scanner.next().toLowerCase();
            playAgain = response.equals("yes");
        }

        System.out.println("Thank you for Playing! Your total score is: " + score);
        scanner.close();
    }
}
