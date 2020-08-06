---
title: 데이터 처리 확장 프로그램 배포 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84fc2d2853ce7a6aae77f313ef0f4026ad2f35cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741604"
---
# <a name="deploying-a-data-processing-extension"></a><span data-ttu-id="2c8cf-102">데이터 처리 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="2c8cf-102">Deploying a Data Processing Extension</span></span>
  <span data-ttu-id="2c8cf-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램을 작성하고 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 라이브러리에 컴파일한 후에는 보고서 서버 및 보고서 디자이너에서 이를 찾을 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c8cf-103">Once you have written and compiled your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension into a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] library, you need to make it discoverable by the report server and by Report Designer.</span></span> <span data-ttu-id="2c8cf-104">이 작업은 확장 프로그램을 적절한 디렉터리에 복사하고 해당하는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 구성 파일에 항목을 추가하여 간단히 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c8cf-104">This is as easy as copying the extension to the appropriate directories and adding entries to the appropriate [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration files.</span></span>  
  
## <a name="configuration-file-extension-element"></a><span data-ttu-id="2c8cf-105">구성 파일 확장 프로그램 요소</span><span class="sxs-lookup"><span data-stu-id="2c8cf-105">Configuration-File Extension Element</span></span>  
 <span data-ttu-id="2c8cf-106">보고서 서버나 보고서 디자이너에 배포하는 데이터 처리 확장 프로그램은 구성 파일에 **Extension** 요소로 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c8cf-106">Data processing extensions that you deploy to the report server or Report Designer need to be entered as **Extension** elements in the configuration files.</span></span> <span data-ttu-id="2c8cf-107">이러한 파일은 보고서 서버의 경우 RSReportServer.config이고, 보고서 디자이너의 경우 RSReportDesigner.config입니다.</span><span class="sxs-lookup"><span data-stu-id="2c8cf-107">These files are RSReportServer.config for the report server and RSReportDesigner.config for Report Designer.</span></span>  
  
 <span data-ttu-id="2c8cf-108">다음 표는 데이터 처리 확장 프로그램에 대한 **Extension** 요소의 특성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2c8cf-108">The following table describes the attributes for the **Extension** element for data processing extensions.</span></span>  
  
|<span data-ttu-id="2c8cf-109">attribute</span><span class="sxs-lookup"><span data-stu-id="2c8cf-109">Attribute</span></span>|<span data-ttu-id="2c8cf-110">Description</span><span class="sxs-lookup"><span data-stu-id="2c8cf-110">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="2c8cf-111">확장 프로그램에 대한 고유한 이름입니다(예: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 처리 확장 프로그램의 경우 "SQL" 또는 OLE DB 데이터 처리 확장 프로그램의 경우 "OLEDB").</span><span class="sxs-lookup"><span data-stu-id="2c8cf-111">A unique name for the extension, for example, "SQL" for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data processing extension or "OLEDB" for the OLE DB data processing extension.</span></span> <span data-ttu-id="2c8cf-112">`Name` 특성의 최대 길이는 255자입니다.</span><span class="sxs-lookup"><span data-stu-id="2c8cf-112">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="2c8cf-113">이름은 구성 파일의 **Extension** 요소에 있는 모든 항목 중에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c8cf-113">The name must be unique among all entries within the **Extension** element of a configuration file.</span></span>|  
|`Type`|<span data-ttu-id="2c8cf-114">정규화된 네임스페이스와 어셈블리 이름을 포함하는 쉼표로 구분된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="2c8cf-114">A comma-separated list that includes the fully qualified namespace along with the name of the assembly.</span></span>|  
|`Visible`|<span data-ttu-id="2c8cf-115">`false` 값은 데이터 처리 확장 프로그램이 사용자 인터페이스에 표시되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2c8cf-115">A value of `false` indicates that the data processing extension should not be visible in user interfaces.</span></span> <span data-ttu-id="2c8cf-116">이 특성이 포함되지 않을 경우 기본값은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="2c8cf-116">If the attribute is not included, the default value is `true`.</span></span>|  
  
 <span data-ttu-id="2c8cf-117">RSReportServer.config 또는 RSReportDesigner.config 파일에 대한 자세한 내용은 [Reporting Services 구성 파일](../../report-server/reporting-services-configuration-files.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c8cf-117">For more information about the RSReportServer.config or RSReportDesigner.config files, see [Reporting Services Configuration Files](../../report-server/reporting-services-configuration-files.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c8cf-118">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="2c8cf-118">In This Section</span></span>  
  
|<span data-ttu-id="2c8cf-119">항목</span><span class="sxs-lookup"><span data-stu-id="2c8cf-119">Topic</span></span>|<span data-ttu-id="2c8cf-120">설명</span><span class="sxs-lookup"><span data-stu-id="2c8cf-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2c8cf-121">방법: 보고서 서버에 데이터 처리 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="2c8cf-121">How to: Deploy a Data Processing Extension to a Report Server</span></span>](deploying-a-data-processing-extension-to-a-report-server.md)|<span data-ttu-id="2c8cf-122">데이터 처리 확장 프로그램을 보고서 서버에 배포하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2c8cf-122">Describes how to deploy your data processing extension to a report server.</span></span>|  
|[<span data-ttu-id="2c8cf-123">방법: 보고서 디자이너에 데이터 처리 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="2c8cf-123">How to: Deploy a Data Processing Extension to Report Designer</span></span>](deploying-a-data-processing-extension-to-report-designer.md)|<span data-ttu-id="2c8cf-124">데이터 처리 확장 프로그램을 보고서 디자이너에 배포하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2c8cf-124">Describes how to deploy your data processing extension to Report Designer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c8cf-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c8cf-125">See Also</span></span>  
 <span data-ttu-id="2c8cf-126">[Reporting Services 확장](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="2c8cf-126">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="2c8cf-127">[데이터 처리 확장 프로그램 구현](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="2c8cf-127">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="2c8cf-128">Reporting Services 확장 프로그램 라이브러리</span><span class="sxs-lookup"><span data-stu-id="2c8cf-128">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
