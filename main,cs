using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp10
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string Path = @"C:\Users\БексултановД\Downloads\images";
            int k = 0;
            foreach (string item in GetAllFiles(Path))
            {
                Console.WriteLine((k++) + ": " + item);
            }

            int ch = 0;
            Console.WriteLine("Choose format -> ");
            ch = Convert.ToInt32(Console.ReadLine());

            DirectoryInfo dir = new DirectoryInfo(Path);
            int count = dir.GetFiles("*" + GetAllFiles(Path)[ch]).Count();
            Console.WriteLine("This kind of files " + count);

            GetName(Path);


        }

        public static void Exmpl01()
        {
            //FileStream fs1 = new FileStream(@"C:\Users\БексултановД\Downloads\ДЗ\text1.txt", FileMode.Create);

            using (FileStream fs1 = new FileStream(@"C:\Users\БексултановД\Downloads\ДЗ\text1.txt", FileMode.Create))
            {

            }//fs1.Close()

            FileStream fs2 = new FileStream(@"C:\Users\БексултановД\Downloads\ДЗ\text2.txt", FileMode.Create, FileAccess.Write);
            FileStream fs3 = new FileStream(@"C:\Users\БексултановД\Downloads\ДЗ\text3.txt", FileMode.Create, FileAccess.Write, FileShare.None);

            fs3.Close();
        }

        public static void Exampl02()
        {
            FileInfo f = new FileInfo(@"C:\Users\БексултановД\Downloads\ДЗ\text1.txt");

            if (!f.Exists)
            {
                var fs = f.Create(); // = FileStream fs = f.Create();
                fs.Close();
            }

            using (FileStream fs = f.Open(FileMode.Open, FileAccess.ReadWrite, FileShare.None))
            {

            }
        }

        public static void Exampl03()
        {
            DirectoryInfo dir = new DirectoryInfo(".");

            DirectoryInfo dir2 = new DirectoryInfo(@"C:\\Users\\БексултановД\\Downloads\\ДЗ");
        }

        public static void Exampl04()
        {
            DirectoryInfo dir = new DirectoryInfo("C:\\Users\\БексултановД\\Downloads");
            Console.WriteLine(">> Инормация о каталоге <<");
            Console.WriteLine("Полный путь: {0}", dir.FullName);

            foreach (var item in dir.GetFiles())
            {
                Console.WriteLine("--> " + item.Name);
            }
            FileInfo[] fileHtml = dir.GetFiles("*.html", SearchOption.AllDirectories);
        }

        public static void Exampl05()
        {
            string path = @"C:\\Users\\БексултановД\\Downloads\\ДЗ";
            try
            {
                using (StreamReader sr = new StreamReader(path))
                {
                    string line;
                    while ((line = sr.ReadLine()) != null)
                    {
                        Console.WriteLine(line);
                    }
                }

                using (StreamReader sr = new StreamReader(path))
                {
                    char[] array = new char[4];
                    sr.Read(array, 0, 4);
                    Console.WriteLine(array);
                }
            }
            catch (Exception ex)
            {

                throw new Exception("Error" + ex.Message);
            }
        }

        // Лабораторная работа

        public static List<string> GetAllFiles(string path)
        {

            List<string> filesExt = new List<string>();

            if (string.IsNullOrWhiteSpace(path))
            {
                Console.WriteLine("Укажите путь");
            }
            else
            {
                DirectoryInfo dir = new DirectoryInfo(path);

                if (!dir.Exists)
                {
                    Console.WriteLine("Указанный путь не корректен");
                }
                else
                {
                    //Полчить расширения всех файлов
                    
                    foreach (FileInfo item in dir.GetFiles())
                    {
                        if(!filesExt.Contains(item.Extension))
                            filesExt.Add(item.Extension);
                    }

                    //Dictionary<string, FileInfo> fileDic = new Dictionary<string, FileInfo>();

                    //foreach (FileInfo item in dir.GetFiles())
                    //{
                    //    if(!fileDic.ContainsKey(item.Extension))
                    //        fileDic.Add(item.Extension, item);
                    //}

                }
            }

            return filesExt;
        }

        public static void GetName(string path)
        {
            DirectoryInfo dir = new DirectoryInfo(path);

            List<string> names = new List<string>() { "-", "_", };

            foreach (FileInfo f in dir.GetFiles())
            {
                if (f.Name.Contains("_"))
                    f.MoveTo(dir.FullName + @"\" + f.Name.Replace("_", ""));
            }
        }

        public static void Tree(string path)
        {
            DirectoryInfo dir = new DirectoryInfo(path);

            foreach (FileInfo item in dir.GetFiles())
            {
                Console.WriteLine("\t-" + item.Name);
                
            }


        }

        public static void PrintDirName(string path)
        {
            DirectoryInfo dir = new DirectoryInfo(path);

            foreach (DirectoryInfo item in dir.GetDirectories())
            {
                Console.WriteLine("-- {0}", dir.FullName);
                PrintDirName(item.Name);
            }
        }
    }
}
