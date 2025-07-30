# Password-Strength-Checker-java
 a simple Password Strength Checker in Java that checks the strength based on common rules: length, presence of uppercase, lowercase, digits, and special characters.
    import java.util.Scanner;

    public class PasswordStrengthChecker {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("🔐 Enter your password: ");
        String password = sc.nextLine();

        int score = checkStrength(password);

        System.out.println("\nPassword Strength: " + interpretStrength(score));
    }

    public static int checkStrength(String password) {
        int score = 0;

        if (password.length() >= 8) score++;
        if (password.matches(".*[a-z].*")) score++;
        if (password.matches(".*[A-Z].*")) score++;
        if (password.matches(".*\\d.*")) score++;
        if (password.matches(".*[!@#$%^&*()-_+=<>?/{}~|].*")) score++;

        return score;
    }

    public static String interpretStrength(int score) {
        switch (score) {
            case 5:
                return "🟢 Very Strong";
            case 4:
                return "🟡 Strong";
            case 3:
                return "🟠 Medium";
            case 2:
                return "🔴 Weak";
            default:
                return "⚠️ Very Weak";
        }
    }
}
