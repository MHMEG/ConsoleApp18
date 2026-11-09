namespace ConsoleApp18
{
    internal class Program
    {
        static void Main(string[] args)
        {

            List<int> numbers = new List<int>();


            bool running = true;

            while (running)
            {
                Console.WriteLine("P - Print numbers");
                Console.WriteLine("A - Add a number");
                Console.WriteLine("M - Display mean of the numbers");
                Console.WriteLine("S - Display the smallest number");
                Console.WriteLine("L - Display the largest number");
                Console.WriteLine("Q - Quit");

                Console.Write("\nEnter your choice: ");
                string X = Console.ReadLine();

                if (string.IsNullOrWhiteSpace(X))
                {
                    Console.WriteLine("Unknown selection, please try again");
                    continue;
                }

                char M = char.ToUpper(X.Trim()[0]);

                switch (M)
                {
                    case 'P':
                        if (numbers.Count == 0)
                        {
                            Console.WriteLine("[] - the list is empty");
                        }
                        else
                        {
                         
                            string formattedList = string.Join(" ", numbers);
                            Console.WriteLine($"[ {formattedList} ]");
                        }
                        break;

                    case 'A':
                        Console.Write("Enter an integer to add: ");
                        if (int.TryParse(Console.ReadLine(), out int num))
                        {
                            numbers.Add(num);
                            Console.WriteLine($"{num} added");
                        }
                        else
                        {
                            Console.WriteLine("Invalid input. Please enter a valid integer.");
                        }
                        break;

                    case 'M':
                        if (numbers.Count == 0)
                        {
                            Console.WriteLine("Unable to calculate the mean - no data");
                        }
                        else
                        {

                            double mean = numbers.Average();
                            Console.WriteLine($"The mean is {mean}");
                        }
                        break;

                    case 'S':
                        if (numbers.Count == 0)
                        {
                            Console.WriteLine("Unable to determine the smallest number - list is empty");
                        }
                        else
                        {
                            int smallest = numbers.Min();
                            Console.WriteLine($"The smallest number is {smallest}");
                        }
                        break;

                    case 'L':
                        if (numbers.Count == 0)
                        {
                            Console.WriteLine("Unable to determine the largest number - list is empty");
                        }
                        else
                        {
                            int largest = numbers.Max();
                            Console.WriteLine($"The largest number is {largest}");
                        }
                        break;

                    case 'Q':
                        Console.WriteLine("Goodbye");
                        running = false;
                        break;

                    default:
                        Console.WriteLine("Unknown selection, please try again");
                        break;
                }
            }
        }
    }
}
