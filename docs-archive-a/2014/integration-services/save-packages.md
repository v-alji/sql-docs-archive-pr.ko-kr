---
title: 패키지 저장 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 17c1de2c-637f-45c2-a148-79294bae0af4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 102e2c3eab001c230722bf3485d6ea9731aa99a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738512"
---
# <a name="save-packages"></a><span data-ttu-id="98aa7-102">패키지 저장</span><span class="sxs-lookup"><span data-stu-id="98aa7-102">Save Packages</span></span>
  <span data-ttu-id="98aa7-103">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 에서 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너를 사용하여 만든 패키지를 파일 시스템에 XML 파일(.dtsx 파일)로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="98aa7-103">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] you build packages by using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and save the packages to the file system as XML files (.dtsx files).</span></span> <span data-ttu-id="98aa7-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 msdb 데이터베이스나 패키지 저장소에 패키지 XML 파일의 복사본을 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98aa7-104">You can also save copies of the package XML file to the msdb database in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to the package store.</span></span> <span data-ttu-id="98aa7-105">패키지 저장소는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에서 관리하는 파일 시스템 위치에 있는 폴더를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="98aa7-105">The package store represents the folders in the file system location that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages.</span></span>  
  
 <span data-ttu-id="98aa7-106">패키지를 파일 시스템에 저장하면 나중에 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스를 사용하여 패키지를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 또는 패키지 저장소로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98aa7-106">If you save a package to the file system, you can later use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service to import the package to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to the package store.</span></span> <span data-ttu-id="98aa7-107">자세한 내용은 [패키지 가져오기 및 내보내기&#40;SSIS 서비스&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98aa7-107">For more information, see [Import and Export Packages &#40;SSIS Service&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md).</span></span>  
  
 <span data-ttu-id="98aa7-108">또한 **dtutil**명령 프롬프트 유틸리티를 사용하여 파일 시스템과 msdb 간에 패키지를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98aa7-108">You can also use a command prompt utility, **dtutil**, to copy a package between the file system and msdb.</span></span> <span data-ttu-id="98aa7-109">자세한 내용은 [dtutil Utility](dtutil-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98aa7-109">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
### <a name="to-save-a-package"></a><span data-ttu-id="98aa7-110">패키지를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="98aa7-110">To save a package</span></span>  
  
-   [<span data-ttu-id="98aa7-111">파일 시스템에 패키지 저장</span><span class="sxs-lookup"><span data-stu-id="98aa7-111">Save a Package to the File System</span></span>](../../2014/integration-services/save-a-package-to-the-file-system.md)  
  
-   [<span data-ttu-id="98aa7-112">패키지 복사본 저장</span><span class="sxs-lookup"><span data-stu-id="98aa7-112">Save a Copy of a Package</span></span>](../../2014/integration-services/save-a-copy-of-a-package.md)  
  
  
