# Task6
    using System;

    class Program
    {
    static void Main()
    {
        int rows = 3; 
        int cols = 4; 

        int[,] matrix = FillMatrix(rows, cols);
        
        Console.WriteLine("Randomly filled matrix:");
        DisplayMatrix(matrix);
    }

    static int[,] FillMatrix(int rows, int cols)
    {
        int[,] matrix = new int[rows, cols];
        int totalElements = rows * cols;

        if (totalElements < 1)
        {
            Console.WriteLine("Invalid matrix size.");
            return null;
        }
        
        int[] uniqueNumbers = new int[totalElements];
        for (int i = 0; i < totalElements; i++)
        {
            uniqueNumbers[i] = i + 1;
        }

        Random random = new Random();
        
        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < cols; j++)
            {
                int randomIndex = random.Next(0, totalElements);
                
                matrix[i, j] = uniqueNumbers[randomIndex];
                Swap(ref uniqueNumbers[randomIndex], ref uniqueNumbers[totalElements - 1]);
                totalElements--;
            }
        }

        return matrix;
    }

    static void Swap(ref int a, ref int b)
    {
        int temp = a;
        a = b;
        b = temp;
    }

    static void DisplayMatrix(int[,] matrix)
    {
        if (matrix == null)
            return;

        int rows = matrix.GetLength(0);
        int cols = matrix.GetLength(1);

        for (int i = 0; i < rows; i++)
        {
            for (int j = 0; j < cols; j++)
            {
                Console.Write(matrix[i, j] + "\t");
            }
            Console.WriteLine();
        }
    }
    }  
