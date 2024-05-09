# Ejercicios-C-o-Python-F-brica-Abstracta-y-Fachada-en-C-o-python
# Nombre: Armando Montiel Garcia #20210602
# Descripción de la Actividad
Objetivo: Implementar los patrones de diseño Fábrica Abstracta y Fachada para facilitar la creación y manejo de diferentes modelos de celulares en una tienda virtual.
# CODIGO:
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using static System.Net.Mime.MediaTypeNames;

namespace ConsoleApp1
{
    // Interfaz para la creación de productos
    interface IFactory
    {
        IPhone CreatePhone();
        ITablet CreateTablet();
    }

    // Productos específicos para Samsung
    class SamsungPhone : IPhone
    {
        public void DisplayInfo()
        {
            Console.WriteLine("Samsung Phone created.");
        }
    }

    class SamsungTablet : ITablet
    {
        public void DisplayInfo()
        {
            Console.WriteLine("Samsung Tablet created.");
        }
    }

    // Productos específicos para Apple
    class ApplePhone : IPhone
    {
        public void DisplayInfo()
        {
            Console.WriteLine("Apple Phone created.");
        }
    }

    class AppleTablet : ITablet
    {
        public void DisplayInfo()
        {
            Console.WriteLine("Apple Tablet created.");
        }
    }

    // Interfaz para productos
    interface IPhone
    {
        void DisplayInfo();
    }

    interface ITablet
    {
        void DisplayInfo();
    }

    // Fábrica abstracta para Samsung
    class SamsungFactory : IFactory
    {
        public IPhone CreatePhone()
        {
            return new SamsungPhone();
        }

        public ITablet CreateTablet()
        {
            return new SamsungTablet();
        }
    }

    // Fábrica abstracta para Apple
    class AppleFactory : IFactory
    {
        public IPhone CreatePhone()
        {
            return new ApplePhone();
        }

        public ITablet CreateTablet()
        {
            return new AppleTablet();
        }
    }

    // Fachada para la tienda de celulares
    class MobileStoreFacade
    {
        private readonly IFactory _factory;

        public MobileStoreFacade(IFactory factory)
        {
            _factory = factory;
        }

        public void OrderPhone()
        {
            IPhone phone = _factory.CreatePhone();
            Console.WriteLine("Phone ordered:");
            phone.DisplayInfo();
        }

        public void OrderTablet()
        {
            ITablet tablet = _factory.CreateTablet();
            Console.WriteLine("Tablet ordered:");
            tablet.DisplayInfo();
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Utilizar la fábrica de Samsung
            IFactory samsungFactory = new SamsungFactory();
            MobileStoreFacade samsungStore = new MobileStoreFacade(samsungFactory);

            samsungStore.OrderPhone();
            samsungStore.OrderTablet();

            // Utilizar la fábrica de Apple
            IFactory appleFactory = new AppleFactory();
            MobileStoreFacade appleStore = new MobileStoreFacade(appleFactory);

            appleStore.OrderPhone();
            appleStore.OrderTablet();
            Console.ReadKey();
        }
    }
}

![image](https://github.com/ArmandoMontielGarcia1/Ejercicios-C-o-Python-F-brica-Abstracta-y-Fachada-en-C-o-python/assets/144396511/347a8011-81ed-41c8-aee2-eea31a8c0bbd)
