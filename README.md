# Temperature-Converter
package pg3;
import java.util.Scanner;
public class TemperatureConverter {

	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);

        // Display instructions
        System.out.println("Welcome to Temperature Converter!");
        System.out.println("Enter a temperature value and specify the unit (C or F).");

        while (true) {
            // Prompt user for temperature value
            System.out.print("Enter temperature value: ");
            double temperature = getTemperature(scanner);

            // Prompt user for unit
            System.out.print("Enter unit (C or F): ");
            String unit = getUnit(scanner);

            // Convert temperature based on unit
            if (unit.equalsIgnoreCase("C")) {
                double convertedTemp = celsiusToFahrenheit(temperature);
                System.out.printf("%.2f°C is %.2f°F\n", temperature, convertedTemp);
            } else if (unit.equalsIgnoreCase("F")) {
                double convertedTemp = fahrenheitToCelsius(temperature);
                System.out.printf("%.2f°F is %.2f°C\n", temperature, convertedTemp);
            } else {
                System.out.println("Invalid unit entered. Please enter C or F.");
                continue;
            }

            // Ask if the user wants to convert another temperature
            System.out.print("Do you want to convert another temperature? (yes/no): ");
            String choice = scanner.next().toLowerCase();
            if (!choice.equals("yes")) {
                System.out.println("Thank you for using Temperature Converter. Goodbye!");
                break;
            }
            scanner.nextLine(); // consume newline
        }

        scanner.close();
    }

    // Method to get valid temperature input
    private static double getTemperature(Scanner scanner) {
        while (true) {
            try {
                return Double.parseDouble(scanner.nextLine().trim());
            } catch (NumberFormatException e) {
                System.out.print("Invalid input. Please enter a valid temperature value: ");
            }
        }
    }

    // Method to get valid unit input (C or F)
    private static String getUnit(Scanner scanner) {
        while (true) {
            String unit = scanner.nextLine().trim();
            if (unit.equalsIgnoreCase("C") || unit.equalsIgnoreCase("F")) {
                return unit;
            } else {
                System.out.print("Invalid input. Please enter C or F: ");
            }
        }
    }

    // Conversion method: Celsius to Fahrenheit
    private static double celsiusToFahrenheit(double celsius) {
        return (celsius * 9 / 5) + 32;
    }

    // Conversion method: Fahrenheit to Celsius
    private static double fahrenheitToCelsius(double fahrenheit) {
        return (fahrenheit - 32) * 5 / 9;
    }
}
