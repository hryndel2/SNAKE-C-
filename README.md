# SNAKE-C-
Console SNAKE GAME C#
```C#
using System;

class Program
{
    static void Main(string[] args)
    {
        int x = 4, y = 4;
        int xApple = 10, yApple = 10;
        bool xvostik = false;
        int hvost = 0;
        int[] xVost = new int[100]; // массив для хвоста 
        int[] yVost = new int[100];

        while (true)
        {
            ConsoleKeyInfo keyboard = Console.ReadKey(true);
            Console.Clear();
            Console.SetCursorPosition(xApple, yApple); // цвет яблока
            Console.ForegroundColor = ConsoleColor.Red;
            Console.Write("A");
            Console.ResetColor();

            int posicGolovaX = x; // прошлая позиция игрока  
            int posicGolovaY = y;

            switch (keyboard.Key)
            {
                case ConsoleKey.W:
                    y -= 1;
                    break;
                case ConsoleKey.A:
                    x -= 1;
                    break;
                case ConsoleKey.S:
                    y += 1;
                    break;
                case ConsoleKey.D:
                    x += 1;
                    break;
            }

            if (x == xApple && y == yApple)
            {
                Console.Clear();
                Console.SetCursorPosition(0, 0);
                Console.ForegroundColor = ConsoleColor.Yellow;
                Console.WriteLine("Вы собрали яблоко");
                Console.ResetColor();
                hvost += 1; // increase tail length
                xvostik = true;
                Random rand = new Random();
                xApple = rand.Next(0, Console.WindowWidth);
                yApple = rand.Next(0, Console.WindowHeight);
            }

            Console.SetCursorPosition(x, y);
            Console.ForegroundColor = ConsoleColor.Green;   // цвет змеи
            Console.Write("#");
            Console.ResetColor();

            if (xvostik == true) //- P.S я думаю  через bool можно не делать, сразу в  if (x == xApple && y == yApple) закинуть, вместо xvostik = true;
            {
                for (int i = hvost; i > 0; i--)
                {
                    xVost[i] = xVost[i - 1];
                    yVost[i] = yVost[i - 1];
                }
                xVost[0] = posicGolovaX;
                yVost[0] = posicGolovaY;

                for (int i = 0; i < hvost; i++)
                {
                    Console.SetCursorPosition(xVost[i], yVost[i]);
                    Console.ForegroundColor = ConsoleColor.Yellow;   // цвет хвоста 
                    Console.Write("0");
                }
            }
            Console.ResetColor();
        }
    }
}
```
