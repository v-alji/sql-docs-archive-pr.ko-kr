---
title: ReportViewer 컨트롤을 사용하여 Reporting Services 통합 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- ReportViewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 18e28dbf1557bf36106b454738d0c0bfc037f2a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639424"
---
# <a name="integrating-reporting-services-using-the-reportviewer-controls"></a><span data-ttu-id="e7da8-102">ReportViewer 컨트롤을 사용하여 Reporting Services 통합</span><span class="sxs-lookup"><span data-stu-id="e7da8-102">Integrating Reporting Services Using the ReportViewer Controls</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="e7da8-103">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]는 보고서 보기 기능을 응용 프로그램에 통합 하기 위한 두 가지 ReportViewer 컨트롤을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-103">[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] provides two ReportViewer controls for integrating report viewing functionality into your applications.</span></span> <span data-ttu-id="e7da8-104">Windows Forms 기반 애플리케이션용 버전과 Web Forms 애플리케이션용 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-104">There is a version for Windows Forms-based applications and one for Web Forms applications.</span></span> <span data-ttu-id="e7da8-105">각 컨트롤은 유사한 기능을 제공하지만 개별 환경에 맞게 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-105">Each control provides similar functionality but each is designed to target their individual environments.</span></span> <span data-ttu-id="e7da8-106">두 컨트롤 모두 보고서 서버에 배포 되었거나 (원격 처리 모드)가 설치 되지 않은 컴퓨터에 복사 된 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (로컬 처리 모드) 보고서를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-106">Both controls can process reports that have been deployed to a report server (remote processing mode) or have been copied to a computer where [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] has not been installed (local processing mode).</span></span>  
  
 <span data-ttu-id="e7da8-107">ReportViewer 컨트롤에는 화면 해상도가 다른 여러 디바이스에 동적으로 채택할 수 있는 기본 제공 지원이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-107">The ReportViewer control does not include built-in support for dynamically adapting to different devices with different screen resolutions.</span></span>  
  
## <a name="remote-processing-mode"></a><span data-ttu-id="e7da8-108">원격 처리 모드</span><span class="sxs-lookup"><span data-stu-id="e7da8-108">Remote Processing Mode</span></span>  
 <span data-ttu-id="e7da8-109">원격 처리 모드는 보고서 서버에 배포된 보고서를 보는 데 권장되는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-109">Remote processing mode is the preferred method for viewing reports that have been deployed to a report server.</span></span> <span data-ttu-id="e7da8-110">원격 처리 모드는 다음과 같은 이점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-110">Remote processing mode provides the following advantages:</span></span>  
  
-   <span data-ttu-id="e7da8-111">보고서가 보고서 서버에서 처리되므로 원격 처리는 보고서 실행을 위한 최적화된 솔루션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-111">Remote processing provides an optimized solution for running reports because the report is processed by the report server.</span></span>  
  
-   <span data-ttu-id="e7da8-112">모든 처리가 보고서 서버에서 수행되므로 보고서 요청을 스케일 아웃 배포의 여러 보고서 서버 또는 수직 확장 시나리오의 여러 프로세서가 있는 서버에서 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-112">Because all processing is handled by the report server, a report request can be processed by multiple report servers in a scale-out deployment or a server that has multiple processors in a scale-up scenario.</span></span>  
  
 <span data-ttu-id="e7da8-113">또한 원격 모드에서 보고서를 실행하면 모든 렌더링 및 데이터 확장 프로그램을 포함하여 보고서 서버의 전체 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-113">In addition, reports run in remote mode can utilize the full functionality of the report server including all rendering and data extensions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7da8-114">원격 처리 모드에서 실행될 때 ReportViewer 컨트롤에서 사용 가능한 확장 프로그램 목록은 보고서 서버에 설치된 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 버전에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-114">The list of extensions available to the ReportViewer control when it is running in remote processing mode depends on the edition of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] that is installed on the report server.</span></span>  
  
## <a name="local-processing-mode"></a><span data-ttu-id="e7da8-115">로컬 처리 모드</span><span class="sxs-lookup"><span data-stu-id="e7da8-115">Local Processing Mode</span></span>  
 <span data-ttu-id="e7da8-116">로컬 처리 모드는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 가 설치되지 않은 경우 보고서를 보고 렌더링하기 위한 대체 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-116">Local processing mode provides an alternative method for viewing and rendering reports when [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not installed.</span></span> <span data-ttu-id="e7da8-117">원격 처리와 달리 보고서 서버에서 제공하는 기능 중 일부만 컨트롤에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-117">Unlike remote processing only a subset of the functionality provided by the report server is available in the control.</span></span> <span data-ttu-id="e7da8-118">로컬 처리 모드에서 데이터 처리는 컨트롤에서 수행되지 않고 호스팅 애플리케이션에서 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-118">In local processing mode, data processing is not handled by the control but rather implemented by the hosting application.</span></span> <span data-ttu-id="e7da8-119">그러나 보고서 처리는 컨트롤 자체에서 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-119">However report processing is handled by the control itself.</span></span> <span data-ttu-id="e7da8-120">로컬 처리 모드에서는 PDF, Excel, Word 및 이미지 렌더링 확장 프로그램만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7da8-120">In local processing mode, only the PDF, Excel, Word, and Image rendering extensions are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7da8-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7da8-121">See Also</span></span>  
 <span data-ttu-id="e7da8-122">[응용 프로그램에 Reporting Services 통합](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="e7da8-122">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 [<span data-ttu-id="e7da8-123">Visual Studio를 사용 하 여 SSRS 보고서 만들기 (블로그)</span><span class="sxs-lookup"><span data-stu-id="e7da8-123">Create SSRS Reports Using Visual Studio (Blog)</span></span>](https://jwcooney.com/2015/01/07/ssrs-basics-set-up-visual-studio-to-write-a-new-ssrs-report/)  
  
  
