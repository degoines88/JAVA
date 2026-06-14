import java.util.InputMismatchException;
import java.util.Scanner;

public class CoffeeSurvey {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        String[] questions = {
            "What is your rating of the dark roast coffee (1-poor, 2-fair, 3-good, 4-excellent, 5-outstanding)? ",
            "What is your rating of the medium roast coffee (1-poor, 2-fair, 3-good, 4-excellent, 5-outstanding)? ",
            "What is your rating of the light roast coffee (1-poor, 2-fair, 3-good, 4-excellent, 5-outstanding)? ",
            "What is your rating of the french vanilla coffee (1-poor, 2-fair, 3-good, 4-excellent, 5-outstanding)? ",
            "What is your rating of the caramel coffee (1-poor, 2-fair, 3-good, 4-excellent, 5-outstanding)? "
        };

        int[] ratings = new int[5];
        int sum = 0;

        for (int i = 0; i < questions.length; i++) {
            while (true) {
                try {
                    System.out.print(questions[i]);
                    int rating = input.nextInt();

                    if (rating < 1 || rating > 5) {
                        throw new IllegalArgumentException("Rating must be between 1 and 5.");
                    }

                    ratings[i] = rating;
                    sum += rating;
                    break;

                } catch (InputMismatchException e) {
                    System.out.println("Invalid input. Please enter a number 1–5.");
                    input.nextLine();
                } catch (IllegalArgumentException e) {
                    System.out.println(e.getMessage());
                }
            }
        }

        System.out.println();
        for (int rating : ratings) {
            for (int s = 0; s < rating; s++) {
                System.out.print("*");
            }
            System.out.println();
        }

        double average = (double) sum / ratings.length;
        System.out.printf("%nYour average rating is %.1f%n", average);
    }
}
