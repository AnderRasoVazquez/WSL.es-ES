---
title: Acerca de WSL 2
description: Acerca de WSL 2 la nueva arquitectura para el subsistema de Windows para Linux
keywords: BashOnWindows, bash, wsl, wsl2, windows, el subsistema de windows para linux, windowssubsystem, ubuntu, debian, suse, windows 10, instalar
author: mscraigloewen
ms.author: mscraigloewen
ms.date: 05/30/2019
ms.topic: article
ms.assetid: 7afaeacf-435a-4e58-bff0-a9f0d75b8a51
ms.custom: seodec18
ms.openlocfilehash: b3b0b1ce0f55fed0b4cf223ccc18a509dcf81788
ms.sourcegitcommit: bb88269eb37405192625fa81ff91162393fb491f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67038135"
---
<span data-ttu-id="553e0-104">WSL 2 es una nueva versión de la arquitectura que se utiliza en el subsistema de Windows para Linux ejecutar los archivos binarios de ELF64 Linux en Windows.</span><span class="sxs-lookup"><span data-stu-id="553e0-104">WSL 2 is a new version of the architecture that powers the Windows Subsystem for Linux to run ELF64 Linux binaries on Windows.</span></span> <span data-ttu-id="553e0-105">Son sus objetivos principales aumentar el rendimiento del sistema de archivos, así como la adición de compatibilidad de llamadas completa del sistema.</span><span class="sxs-lookup"><span data-stu-id="553e0-105">Its primary goals are to increase file system performance, as well as adding full system call compatibility.</span></span> <span data-ttu-id="553e0-106">Esta nueva arquitectura cambia cómo interactúan estos archivos binarios de Linux con Windows y el hardware del equipo, pero sigue ofreciendo la misma experiencia de usuario como en WSL 1 (la versión actual de ampliamente disponible).</span><span class="sxs-lookup"><span data-stu-id="553e0-106">This new architecture changes how these Linux binaries interact with Windows and your computer’s hardware, but still provides the same user experience as in WSL 1 (the current widely available version).</span></span> <span data-ttu-id="553e0-107">Linux individual distribuciones se pueden ejecutar como una distribución de WSL 1, o como una distribución de WSL 2, puede ser actualizado o degradado en cualquier momento, y puede ejecutar en paralelo de distribuciones WSL 1 y 2 de WSL.</span><span class="sxs-lookup"><span data-stu-id="553e0-107">Individual Linux distros can be run either as a WSL 1 distro, or as a WSL 2 distro, can be upgraded or downgraded at any time, and you can run WSL 1 and WSL 2 distros side by side.</span></span> <span data-ttu-id="553e0-108">WSL 2 utiliza una arquitectura totalmente nueva que usa un kernel de Linux real.</span><span class="sxs-lookup"><span data-stu-id="553e0-108">WSL 2 uses an entirely new architecture that uses a real Linux kernel.</span></span>

## <a name="linux-kernel-in-wsl-2"></a><span data-ttu-id="553e0-109">Kernel de Linux en WSL 2</span><span class="sxs-lookup"><span data-stu-id="553e0-109">Linux kernel in WSL 2</span></span>

<span data-ttu-id="553e0-110">El kernel de Linux en WSL 2 se basa en casa de la bifurcación estable más reciente, según el origen está disponible en kernel.org. Este kernel ha sido optimizado especialmente para WSL 2.</span><span class="sxs-lookup"><span data-stu-id="553e0-110">The Linux kernel in WSL 2 is built in house from the latest stable branch, based on the source available at kernel.org. This kernel has been specially tuned for WSL 2.</span></span> <span data-ttu-id="553e0-111">Se ha optimizado para que el tamaño y rendimiento para proporcionar una experiencia increíble de Linux en Windows y se atenderán a través de actualizaciones de Windows, lo que significa que obtendrá las últimas revisiones de seguridad y mejoras de kernel sin necesidad de administrar usted mismo.</span><span class="sxs-lookup"><span data-stu-id="553e0-111">It has been optimized for size and performance to give an amazing Linux experience on Windows and will be serviced through Windows updates, which means you will get the latest security fixes and kernel improvements without needing to manage it yourself.</span></span>

<span data-ttu-id="553e0-112">Además, este kernel estará abierto.</span><span class="sxs-lookup"><span data-stu-id="553e0-112">Additionally this kernel will be open source.</span></span> <span data-ttu-id="553e0-113">Puede encontrar el código fuente completo para el kernel de Linux [aquí](https://thirdpartysource.microsoft.com/download/Windows%20Subsystem%20for%20Linux%20v2/May%202019/WSLv2-Linux-Kernel-master.zip).</span><span class="sxs-lookup"><span data-stu-id="553e0-113">You can find the full source code for the Linux kernel [here](https://thirdpartysource.microsoft.com/download/Windows%20Subsystem%20for%20Linux%20v2/May%202019/WSLv2-Linux-Kernel-master.zip).</span></span> <span data-ttu-id="553e0-114">Si desea leer más sobre este kernel pueden desproteger [esta entrada de blog](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/) escrito por el equipo que lo crearon.</span><span class="sxs-lookup"><span data-stu-id="553e0-114">If you’d like to read more about this kernel you can check out [this blog post](https://devblogs.microsoft.com/commandline/shipping-a-linux-kernel-with-windows/) written by the team that built it.</span></span>

## <a name="brief-overview-of-the-wsl-2-architecture"></a><span data-ttu-id="553e0-115">Breve descripción de la arquitectura 2 de WSL</span><span class="sxs-lookup"><span data-stu-id="553e0-115">Brief overview of the WSL 2 architecture</span></span>

<span data-ttu-id="553e0-116">WSL 2 usa los más recientes y mejores avances en tecnología de virtualización para ejecutar el kernel de Linux dentro de una máquina virtual de utilidad ligera (VM).</span><span class="sxs-lookup"><span data-stu-id="553e0-116">WSL 2 uses the latest and greatest in virtualization technology to run its Linux kernel inside of a lightweight utility virtual machine (VM).</span></span> <span data-ttu-id="553e0-117">Sin embargo, 2 de WSL no será una experiencia de la máquina virtual tradicionales.</span><span class="sxs-lookup"><span data-stu-id="553e0-117">However, WSL 2 will NOT be a traditional VM experience.</span></span> <span data-ttu-id="553e0-118">Una experiencia de máquina virtual tradicional puede ralentizarse arrancar, está aislada, consume muchos recursos y requiere su tiempo para administrarlo.</span><span class="sxs-lookup"><span data-stu-id="553e0-118">A traditional VM experience can be slow to boot up, is isolated, consumes lots of resources, and requires your time to manage it.</span></span> <span data-ttu-id="553e0-119">WSL 2 no tiene estos atributos.</span><span class="sxs-lookup"><span data-stu-id="553e0-119">WSL 2 does not have these attributes.</span></span> <span data-ttu-id="553e0-120">Le ofrecen las ventajas más destacable de WSL 1: Altos niveles de integración entre Windows y Linux, tiempos de arranque muy rápidas, superficie de recursos pequeña y lo mejor de todo no requerirá ninguna configuración de máquina virtual o la administración.</span><span class="sxs-lookup"><span data-stu-id="553e0-120">It will still give the remarkable benefits of WSL 1: High levels of integration between Windows and Linux, extremely fast boot times, small resource footprint, and best of all will require no VM configuration or management.</span></span> <span data-ttu-id="553e0-121">Aunque WSL 2 usar una máquina virtual, se administra y ejecutar en segundo plano se deja con la misma experiencia de usuario como WSL 1.</span><span class="sxs-lookup"><span data-stu-id="553e0-121">While WSL 2 does use a VM, it will be managed and run behind the scenes leaving you with the same user experience as WSL 1.</span></span>

## <a name="increased-file-io-performance"></a><span data-ttu-id="553e0-122">Archivo de mayor rendimiento de E/S</span><span class="sxs-lookup"><span data-stu-id="553e0-122">Increased file IO performance</span></span>

<span data-ttu-id="553e0-123">Operaciones intensivas de archivo, como clonación de git, npm install, apt actualización, actualización apt y más todo será notablemente más rápido.</span><span class="sxs-lookup"><span data-stu-id="553e0-123">File intensive operations like git clone, npm install, apt update, apt upgrade, and more will all be noticeably faster.</span></span> <span data-ttu-id="553e0-124">El aumento de la velocidad real dependerá de qué aplicación está ejecutando y cómo interactúa con el sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="553e0-124">The actual speed increase will depend on which app you’re running and how it is interacting with the file system.</span></span> <span data-ttu-id="553e0-125">Las versiones iniciales de WSL 2 ejecutan hasta 20 veces más rápido en comparación con 1 WSL desempaquetar un paquete tarball comprimido y alrededor de 2 a 5 veces más rápido cuando se usa la clonación de git, npm install y cmake en varios proyectos.</span><span class="sxs-lookup"><span data-stu-id="553e0-125">Initial versions of WSL 2 run up to 20x faster compared to WSL 1 when unpacking a zipped tarball, and around 2-5x faster when using git clone, npm install and cmake on various projects.</span></span>

## <a name="full-system-call-compatibility"></a><span data-ttu-id="553e0-126">Compatibilidad de llamadas completa del sistema</span><span class="sxs-lookup"><span data-stu-id="553e0-126">Full System Call Compatibility</span></span>

<span data-ttu-id="553e0-127">Los archivos binarios de Linux utilizar llamadas del sistema para realizar muchas funciones, como obtener acceso a archivos, que soliciten memoria, creación de procesos y mucho más.</span><span class="sxs-lookup"><span data-stu-id="553e0-127">Linux binaries use system calls to perform many functions such as accessing files, requesting memory, creating processes, and more.</span></span> <span data-ttu-id="553e0-128">Mientras que 1 WSL usa una capa de traducción que se compiló el equipo de WSL, WSL 2 incluye su propio kernel de Linux con compatibilidad de llamadas completa del sistema.</span><span class="sxs-lookup"><span data-stu-id="553e0-128">Whereas WSL 1 used a translation layer that was built by the WSL team, WSL 2 includes its own Linux kernel with full system call compatibility.</span></span> <span data-ttu-id="553e0-129">Esto presenta un nuevo conjunto completo de aplicaciones que se pueden ejecutar dentro de WSL, como Docker y mucho más.</span><span class="sxs-lookup"><span data-stu-id="553e0-129">This introduces a whole new set of apps that you can run inside of WSL, such as Docker and more.</span></span> <span data-ttu-id="553e0-130">Además, las actualizaciones del kernel de Linux pueden ser inmediatamente listos para agregarse a su equipo, en lugar de esperar el equipo de WSL para implementar los cambios y, a continuación, tener les agregan.</span><span class="sxs-lookup"><span data-stu-id="553e0-130">Additionally, any updates to the Linux kernel can be immediately ready to be added to your computer, rather than waiting for the WSL team to implement the changes and then have them added.</span></span>