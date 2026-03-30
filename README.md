using System;
using System.Reflection;

namespace ReflectionDemo
{
    class Student
    {
        public int Id;
        public string Name;

        public void Display()
        {
            Console.WriteLine("Student Details");
        }

        private void PrivateMethod()
        {
            Console.WriteLine("Private Method");
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Load current assembly (.exe from bin folder)
            Assembly assembly = Assembly.GetExecutingAssembly();

            Console.WriteLine("Assembly Name: " + assembly.FullName);

            // Get all types (classes)
            Type[] types = assembly.GetTypes();

            foreach (Type t in types)
            {
                Console.WriteLine("\nClass: " + t.Name);

                // Fields
                Console.WriteLine(" Fields:");
                foreach (FieldInfo f in t.GetFields())
                {
                    Console.WriteLine("  " + f.Name);
                }

                // Properties
                Console.WriteLine(" Properties:");
                foreach (PropertyInfo p in t.GetProperties())
                {
                    Console.WriteLine("  " + p.Name);
                }

                // Methods
                Console.WriteLine(" Methods:");
                foreach (MethodInfo m in t.GetMethods())
                {
                    Console.WriteLine("  " + m.Name);
                }
            }

            Console.ReadLine();
        }
    }
}
