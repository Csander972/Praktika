# Praktika
Task 3
using System;
using System.Collections.Generic;
using System.Linq;
using System.Runtime.CompilerServices;
using System.Text;
using System.Threading.Tasks;

namespace Task3
{
    class Program
    {
        static void Main(string[] args)
        {
            GetCoordinates(out var x, out var y);

            if (DefineIfBelongs(x, y))
                Console.WriteLine("Точка принадлежит заданной области.\n");
            else
                Console.WriteLine("Точка не принадлежит заданной области.\n");
        }

        private static void GetCoordinates(out double x, out double y)
        {
            while (true)
            {
                try
                {
                    Console.Write("Введите вещественные координаты x и y через пробел: ");
                    var coordinates = Console.ReadLine()?.Split(' ') ?? throw new FormatException();
                    if (coordinates.Length != 2) throw new FormatException();
                    x = Convert.ToDouble(coordinates[0]);
                    y = Convert.ToDouble(coordinates[1]);
                    return;
                }
                catch (Exception ex)
                {
                    if (ex is FormatException)
                        Console.WriteLine("Некорректный ввод. Повторите попытку.");
                    else
                        Console.WriteLine("Непредвиденная ошибка: " + ex.Message);
                }
            }
        }

        private static bool DefineIfBelongs(double x, double y)
        {
            return (y <= 3*x + 2) && (y <= -3*x + 2) && (y >= -1);
        }
    }
}
