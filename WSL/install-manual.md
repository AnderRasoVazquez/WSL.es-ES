---
title: Descargar manualmente el subsistema de Windows para Linux (WSL) distribuciones
description: Instrucciones sobre cómo descargar manualmente el subsistema de Windows para distribuciones de Linux.
keywords: BashOnWindows, bash, WSL, Windows, subsistema de Windows para Linux, WSL, subsistema de Windows, distribución, Ubuntu, openSUSE, SLES, Debian, Kali
ms.date: 07/24/2018
ms.topic: article
ms.assetid: 9281ffa2-4fa9-4078-bf6f-b51c967617e3
ms.custom: seodec18
ms.openlocfilehash: 99215a3bccc3d0b07e8ed4b7629913af3765aec0
ms.sourcegitcommit: d35870009477813aa4c8fe4e401af4bddef4a47c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778824"
---
# <a name="manually-download-windows-subsystem-for-linux-distro-packages"></a>Descargar manualmente el subsistema de Windows para paquetes distribución de Linux

Hay varios escenarios en los que es posible que no pueda (o desee) instalar WSL Linux distribuciones a través de la Microsoft Store. En concreto, es posible que esté ejecutando una SKU de sistema operativo de escritorio de Windows Server o de mantenimiento a largo plazo (LTSC) que no admita Microsoft Store, o que sus administradores o directivas de red corporativa no permitan el uso de Microsoft Store en su entorno.

En estos casos, aunque WSL está disponible, ¿cómo se descarga e instala Linux distribuciones en WSL si no se puede acceder a la tienda?

> Nota: los **entornos de Shell de línea de comandos, incluidos cmd, PowerShell y Linux/WSL distribuciones, no se pueden ejecutar en el modo Windows 10 S**. Esta restricción existe con el fin de garantizar la integridad y los objetivos de seguridad que ofrece el modo S: lea [esta entrada](https://blogs.msdn.microsoft.com/commandline/2017/05/18/will-linux-distros-run-on-windows-10-s/) para obtener más información.

## <a name="downloading-distros"></a>Descarga de distribuciones

Si la aplicación Microsoft Store no está disponible, puede descargar e instalar manualmente Linux distribuciones haciendo clic en estos vínculos:
* [Ubuntu 18,04](https://aka.ms/wsl-ubuntu-1804)
* [ARM de Ubuntu 18,04](https://aka.ms/wsl-ubuntu-1804-arm)
* [Ubuntu 16,04](https://aka.ms/wsl-ubuntu-1604)
* [Debian GNU/Linux](https://aka.ms/wsl-debian-gnulinux)
* [Kali Linux](https://aka.ms/wsl-kali-linux-new)
* [OpenSUSE Leap 42](https://aka.ms/wsl-opensuse-42)
* [SUSE Linux Enterprise Server 12](https://aka.ms/wsl-sles-12)
* [Fedora Remix for WSL](https://github.com/WhitewaterFoundry/WSLFedoraRemix/releases/)

Esto hará que los paquetes de `<distro>.appx` se descarguen en una carpeta de su elección. Siga las [instrucciones de instalación](#installing-your-distro) para instalar los distribución descargados.

## <a name="downloading-distros-via-the-command-line"></a>Descarga de distribuciones a través de la línea de comandos
Si lo prefiere, también puede descargar los distribución preferidos a través de la línea de comandos:

 ### <a name="download-using-powershell"></a>Descargar con PowerShell
 Para descargar distribuciones con PowerShell, use el cmdlet [Invoke-WebRequest](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/invoke-webrequest) . A continuación se muestra una instrucción de ejemplo para descargar ubuntu 16,04.

```powershell
Invoke-WebRequest -Uri https://aka.ms/wsl-ubuntu-1604 -OutFile Ubuntu.appx -UseBasicParsing
```

> [!TIP]
> Si la descarga tarda mucho tiempo, desactive la barra de progreso estableciendo `$ProgressPreference = 'SilentlyContinue'`

### <a name="download-using-curl"></a>Descargar mediante curl
La actualización de Spring 2018 de Windows 10 (o posterior) incluye la popular [utilidad de línea de comandos de curl](https://curl.haxx.se/) con la que puede invocar solicitudes web (es decir, HTTP GET, post, Put, etc.) desde la línea de comandos. Puede usar `curl.exe` para descargar el distribuciones anterior:

```console
curl.exe -L -o ubuntu-1604.appx https://aka.ms/wsl-ubuntu-1604
```

En el ejemplo anterior, se ejecuta `curl.exe` (no solo `curl`) para asegurarse de que, en PowerShell, se invoca el ejecutable de curl real, no el alias de curl de PowerShell para [Invoke-WebRequest](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-6) .

> Nota: el uso de `curl` podría ser preferible si tiene que invocar o crear scripts de pasos de descarga con el shell de CMD o `.bat`  /  scripts `.cmd`.

## <a name="installing-your-distro"></a>Instalación de distribución
Si usa Windows 10, puede instalar el distribución con PowerShell. Simplemente vaya a la carpeta que contiene el distribución descargado de arriba y, en ese directorio, ejecute el siguiente comando, donde `app_name` es el nombre del archivo distribución. appx.  
```Powershell
Add-AppxPackage .\app_name.appx
```

Si usa Windows Server, puede encontrar las instrucciones de instalación en la página de documentación de [Windows Server](install-on-server.md) .

Una vez instalado el distribución, consulte la página [pasos de inicialización](initialize-distro.md) para inicializar el nuevo distribución.
