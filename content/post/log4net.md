+++
author = "Hugo Roca"
date =  "2018-05-20"
linktitle = "Registro de errores con Log4Net"
title =  "Registro de errores con Log4Net"
description = "Si eres un gran desarrollador sabrás que todo software debe de tener un LOG, en esta oportunidad te muestro un aplicativo de como se hace uno."
weight = "10"
image =  "img/log4net.jpg"
authorAvatar =  "hugo.jpeg"
nomenu = "main"
tags = [
    "csharp",
    "sqlserver"
]
+++

Si eres un gran desarrollador sabrás que todo software debe de tener un LOG, en esta oportunidad te muestro un aplicativo de como se hace uno.


## Paso 1
Crear un proyecto de consola en visual studio

## Paso 2
Agregar el siguiente paguete nuget:
![](https://image.ibb.co/bNiXep/1.png)

## Paso 3
Agregar una clase a la cual llamaremos ```LogHelper.cs```
```
namespace Log4Net
{
    public class LogHelper
    {
        public static log4net.ILog GetLogger([CallerFilePath]string filename = "")
        {
            return log4net.LogManager.GetLogger(filename);
        }
    }
}
```

## Paso 4
Para configurar el archivo ```.txt``` en donde se registrarán los errores, configuramos lo siguiente en el ```app.config```
```
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section name="log4net" type="log4net.Config.Log4NetConfigurationSectionHandler, log4net" />
  </configSections>
  <log4net>
    <appender name="RollingFileAppender" type="log4net.Appender.RollingFileAppender">
      <lockingModel type="log4net.Appender.FileAppender+MinimalLock"/>
      <file value="C:\Logs\" />
      <datePattern value="dd.MM.yyyy'.log'" />
      <appendToFile value="true" />
      <rollingStyle value="Composite" />
      <maximumFileSize value="10MB" />
      <maxSizeRollBackups value="5" />
      <staticLogFileName value="false" />
      <layout type="log4net.Layout.PatternLayout">
        <conversionPattern 
            value="::::::::::::::::::::::::::::::::::::::::
                %newlineFecha: %date{MMMM dd, yyyy HH:mm:ss, fff} 
                %newlineRuta: %location 
                %newlineLinea: %line 
                %newlineMetodo: %method 
                %newlineTipo: %level 
                %newlineMensaje: %message%
                newline%exception
                %newline::::::::::::::::::::::::::::::::::::::::" />
      </layout>
    </appender>
    <root>
      <level value="DEBUG" />
      <appender-ref ref="ConsoleAppender" />
      <appender-ref ref="RollingFileAppender" />
    </root>
  </log4net>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
</configuration>
```

## Paso 5
Nos situamos en el archivo ```program.cs``` y hacemos siguiente:
```
[assembly: log4net.Config.XmlConfigurator(Watch = true)]

namespace Log4Net
{
    class Program
    {
        private static readonly log4net.ILog log = LogHelper.GetLogger();

        static void Main(string[] args)
        {
            divide();
            Console.ReadLine();
            void divide()
            {
                try
                {
                    var i = 0;
                    var a = 5 / i;
                }
                catch (DivideByZeroException ex)
                {
                    log.Error("división entro 0", ex);
                }

            }
        }

    }
}
```

Ejecutamos y comprobamos el error registrado, como lo configuramos en el paso 4 ```<file value="C:\Logs\" />```, buscamos la ruta y vemos el error.
![](https://image.ibb.co/itOes9/2.png)

### Para terminar
En este repo, existe ejemplos de como registrar los errores en base de datos

1. Clonar [Log4Net](https://github.com/PORTAFOLIO-PROYECTOS/LOG4NET_PRINCIPIANTE_A_FIN)
2. Abrir la solución y explorar el código fuente

Comenta, disfruta y comparte! 