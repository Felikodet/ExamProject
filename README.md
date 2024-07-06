import java.util.Scanner;

public class ExamProject {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        double[] courseworkResults = new double[5]; // Assuming 5 coursework assessments
        
        do {
            // Display menu
            System.out.println("\n===== Exam Program Menu =====");
            System.out.println("1. View coursework results");
            System.out.println("2. View exam results");
            System.out.println("3. Exit the program");
            System.out.print("Enter your choice (1-3): ");
            
            // Get user choice
            int choice = scanner.nextInt();
            
            switch (choice) {
                case 1:
                    // Option 1: View coursework results
                    courseworkResults = inputCourseworkResults();
                    break;
                    
                case 2:
                    // Option 2: View exam results
                    double examResult = inputExamResult();
                    double totalScore = calculateTotalScore(courseworkResults, examResult);
                    System.out.println("Final exam result: " + examResult);
                    System.out.println("Coursework total: " + calculateCourseworkTotal(courseworkResults));
                    System.out.println("Total score: " + totalScore);
                    break;
                    
                case 3:
                    // Option 3: Exit the program
                    System.out.println("Exiting the program...");
                    scanner.close();
                    System.exit(0);
                    break;
                    
                default:
                    System.out.println("Invalid choice. Please enter a number from 1 to 3.");
            }
            
        } while (true);
    }

    public static double[] inputCourseworkResults() {
        Scanner scanner = new Scanner(System.in);
        double[] courseworkResults = new double[5]; // Array to store results of 5 assessments
        
        System.out.println("Enter results for coursework assessments:");
        for (int i = 0; i < courseworkResults.length; i++) {
            System.out.print("Enter result for assessment " + (i + 1) + ": ");
            courseworkResults[i] = scanner.nextDouble();
        }
        
        return courseworkResults;
    }

    public static int countCourseworkAssessments() {
        // Counting function using a for-loop
        // Assuming 5 assessments for simplicity
        return 5;
    }

    public static boolean hasCompletedEnoughCoursework(double[] courseworkResults) {
        // Decision function to determine if student has done 2/3 of coursework
        int numAssessments = countCourseworkAssessments();
        if (courseworkResults.length < numAssessments * 2 / 3) {
            System.out.println("Student has not completed enough coursework. Student needs to repeat.");
            return false;
        } else {
            System.out.println("Student has completed enough coursework.");
            return true;
        }
    }

    public static double inputExamResult() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter exam result (0-100): ");
        return scanner.nextDouble();
    }

    public static double calculateCourseworkTotal(double[] courseworkResults) {
        // Calculate coursework total (ass1 + ass2 + ass3 + cat1 + cat2)
        double courseworkTotal = 0.0;
        for (double result : courseworkResults) {
            courseworkTotal += result;
        }
        return courseworkTotal;
    }

    public static double calculateTotalScore(double[] courseworkResults, double examResult) {
        // Calculate total score (final exam + coursework)
        double courseworkTotal = calculateCourseworkTotal(courseworkResults);
        return examResult * 0.5 + courseworkTotal * 0.5;
    }
}


