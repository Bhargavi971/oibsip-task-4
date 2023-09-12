import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

class User {
    private String username;
    private String password;

    public User(String username, String password) {
        this.username = username;
        this.password = password;
    }

    public boolean authenticate(String inputPassword) {
        return this.password.equals(inputPassword);
    }

    public String getUsername() {
        return username;
    }
}

public class OnlineExamSystem {
    private static Map<String, User> users = new HashMap<>();

    public static void main(String[] args) {
        // Create some sample users (in a real system, you would fetch this from a database).
        users.put("student1", new User("student1", "password1"));
        users.put("admin", new User("admin", "adminpass"));

        Scanner scanner = new Scanner(System.in);
        System.out.println("Welcome to the Online Examination System!");

        while (true) {
            System.out.print("Enter your username: ");
            String username = scanner.nextLine();
            System.out.print("Enter your password: ");
            String password = scanner.nextLine();

            User user = users.get(username);

            if (user != null && user.authenticate(password)) {
                System.out.println("Login successful. Welcome, " + user.getUsername() + "!");
                // Implement menu options for students and administrators here.
                // For example, students can take exams, and administrators can manage questions.
                break;
            } else {
                System.out.println("Invalid username or password. Please try again.");
            }
        }

        scanner.close();
    }
}
