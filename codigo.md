# 1_U2-Abstract-Factory

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace _1_U2_Abstract_Factory
{
        public abstract class MaterialFactory
        {
            public abstract Guia CrearGuia();
            public abstract Examen CrearExamen();
        }
        public abstract class Guia
        {
            public abstract void Mostrar();
        }
        public abstract class Examen
        {
            public abstract void Aplicar();
        }
```

 ## presencial
```csharp
        public class GuiaImpresa : Guia
        {
            public override void Mostrar()
            {
                Console.WriteLine("Mostrando la guia impresa");
            }
        }

        public class ExamenEnPapel : Examen
        {
            public override void Aplicar()
            {
                Console.WriteLine("Se aplica examen en papel");
            }
        }

        public class MaterialPresencialFactory : MaterialFactory
        {
            public override Guia CrearGuia()
            {
                return new GuiaImpresa();
            }
            public override Examen CrearExamen()
            {
                return new ExamenEnPapel();
            }
        }
```

## Virtual

````csharp
 public class GuiaPDF : Guia
        {
            public override void Mostrar()
            {
                Console.WriteLine("Mostrando la guia PDF");
            }
        }

        public class ExamenOnline : Examen
        {
            public override void Aplicar()
            {
                Console.WriteLine("Se aplica examen en linea");
            }
        }

        public class MaterialVirtualFactory : MaterialFactory
        {
            public override Guia CrearGuia()
            {
                return new GuiaPDF();
            }

            public override Examen CrearExamen()
            {
                return new ExamenOnline();
            }
        }
````

## Hibrida
````csharp
public class GuiaHibrida : Guia
        {
            public override void Mostrar()
            {
                Console.WriteLine("Mostrando la guia en modalidad hibrida");
            }
        }
        public class ExamenMixto : Examen
        {
            public override void Aplicar()
            {
                Console.WriteLine("Se aplica examen mixto");
            }
        }
        public class MaterialHibridaFactory : MaterialFactory
        {
            public override Guia CrearGuia()
            {
                return new GuiaHibrida();
            }

            public override Examen CrearExamen()
            {
                return new ExamenMixto();
            }
        }

       
        internal class Program
        {
            static void Main(string[] args)
            {
                MaterialFactory fabrica;
                fabrica = new MaterialPresencialFactory();
                Guia guia = fabrica.CrearGuia();
                Examen examen = fabrica.CrearExamen();
                guia.Mostrar();
                examen.Aplicar();
                Console.WriteLine("");

                fabrica = new MaterialVirtualFactory();
                guia = fabrica.CrearGuia();
                examen = fabrica.CrearExamen();
                guia.Mostrar();
                examen.Aplicar();
                Console.WriteLine("");

                fabrica = new MaterialHibridaFactory();
                guia = fabrica.CrearGuia();
                examen = fabrica.CrearExamen();
                guia.Mostrar();
                examen.Aplicar();
                Console.ReadKey();
            }
        }
    }

````

## Captura
<img width="409" height="176" alt="image" src="https://github.com/user-attachments/assets/a26af3f7-eb87-478d-a341-7b6b90070e53" />
