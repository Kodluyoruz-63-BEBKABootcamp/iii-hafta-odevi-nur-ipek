# Extension Methods in C#
## Introduction
 Extension Methods, as the name suggests, are methods used to extend the functionality of any C# types without having to directly modify and re-compile the original type itself.

## Use Case
Extension methods are typically used whenever there is a need to add certain functionality to any C# types which are available as an external library or ".dll". In cases where the source code of external library is unavailable or restricted for modifications, C# extension methods can be used to extend the functionality of certain class or struct provided in that external library.

## Example Scenario
Consider the following scenario, C# has an inbuilt Class Random in System Namespace which can be used to generate random numbers. Next() method defined in Random class generates a random number.

Now, let's say we want to generate random English alphabet instead of random number. However, there is no in-built method in the Random class which allows us to do that. And since Random is an inbuilt type provided by C#, we can not directly modify the class itself and add a new method to generate random alphabet.

**Random number generation using inbuilt method in Random Class**

    using System;  

    namespace ExtensionMethodDemo  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {       
                Random rnd = new Random();
                // Next() method returns a random integer
                int randomNum = rnd.Next(); 
                Console.WriteLine("random Num " + randomNum);
            }
        }
    }
    
**Output**: random Num 1854662654

**Adding NextAlphabet() extension method to the Random Class**

We can create an Extension Method named NextAlphabet() and use it as if it was defined in the Random class itself.

  using System;
  namespace ExtensionMethodDemo
  {
     public static class ExtensionMethods
     {
        // Extension Method which return random english letter
        public static char NextAlphabet(this Random rnd)
        {
           int rndIndex = rnd.Next(0, 26);
           return (char)('a' + rndIndex);
        }
      }
  }


**Using NextAlphabet() Extension Method:**

    using System; 
    namespace ExtensionMethodDemo
    {
        class Program
        {
            static void Main(string[] args)
            {   
                Random rnd = new Random();
            // Next() method returns a random integer
                int randomNum = rnd.Next(); 
                Console.WriteLine("random Num " + randomNum);

            // EXTENSION METHOD NextAlphabet()
                // Extension method are called exactly like instance method
                char randomLetter = rnd.NextAlphabet();
                Console.WriteLine("Random Letter: " + randomLetter);
            }
        }
    }
    
**Output:**

random Num 1066262963
Random Letter: q


## Points to note about C# extension methods
C# extension methods must be defined in a static class. In the example above, all extension methods are inside static class ExtensionMethods.
C# extension methods must be defined as static.
Unlike regular static method in C#, extension method must have the first parameter preceded by "this" keyword. The first parameter with "this" keyword specifies the type for which the extension method is being added. In the example below, we are adding NextAlphabet() extension method to the type of System.Random class.
    // Note the static and this Keyword in Extension Method Signature
    
    public static char NextAlphabet(this Random rnd)
    {
        // ...
    }
    
Even though extension methods are defined as static method, they are invoked exactly like an instance method. An instance of that type needs to be created before calling extension methods. Since first parameter with the "this" keyword specifies the type for which extension method is defined, it shouldn't be passed as an argument when calling the extension method.
    // Calling an extension method
    
    Random rnd = new Random();
    
    // invoked like any other instance method of Random Class
    
    
    char randomLetter = rnd.NextAlphabet();
    
## Extension method with additional parameter
Any additional parameters to the extension methods must be added to the parameter list after the first parameter.

Now let's create an extension method for Random Class which returns a random item from any given list passed as an argument.

    public static string PickRandom(this Random rnd, List<string> list)
    {
        int rndIndex = rnd.Next(0, list.Count);
        return list[rndIndex];
    }
    
**Using PickRandom() Extension Method**

    using System;
    using System.Collections.Generic;
    namespace ExtensionMethodDemo
    {
        class Program
        {
            static void Main(string[] args)
            {   
            Random rnd = new Random();
                List<string> names = new List<string> { "Ronaldo", "Hazard", "Messi", "Lampard" };
                // list names is passed as an argument to the extension method
            string randomName = rnd.PickRandom(names);
                Console.WriteLine("Random Name: " + randomName);
            }
        }
    }
Output: Random Name: Lampard



references : https://dev.to/99darshan/introduction-to-extension-methods-in-c-b13 
