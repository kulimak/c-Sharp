Fájlból olvasás

using System;
using System.IO;
using System.Collections.Generic;

class Program
{
    // Egyszerű osztály az adatok tárolására
    class Person
    {
        public string Name { get; set; }
        public int Age { get; set; }
    }
    static void Main()
    {
        string filePath = "adatok.csv";  // A beolvasandó fájl neve
        if (!File.Exists(filePath))
        {
            Console.WriteLine("A fájl nem található: " + filePath);
            return;
        }
        List<Person> people = new List<Person>();
        // Fájl soronkénti beolvasása
        foreach (var line in File.ReadLines(filePath))
        {
            var parts = line.Split(',');
            if (parts.Length == 2 && int.TryParse(parts[1], out int age))
            {
                people.Add(new Person { Name = parts[0], Age = age });
            }
        }
        // Kiírás a konzolra
        foreach (var person in people)
        {
            Console.WriteLine($"Név: {person.Name}, Kor: {person.Age}");
        }
    }
}
