---
title: SQL Server Management Studio에서 Integration Services 패키지 보기 (SSIS 서비스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- viewing packages
- connections [Integration Services], packages
ms.assetid: 783e653c-0f1f-45ed-b3ef-5ba07b019f27
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4ba86320f1b1a685eab6e80399f3e8c21bd110eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728443"
---
# <a name="view-integration-services-packages-in-sql-server-management-studio-ssis-service"></a><span data-ttu-id="82634-102">SQL Server Management Studio에서 Integration Services 패키지 보기(SSIS 서비스)</span><span class="sxs-lookup"><span data-stu-id="82634-102">View Integration Services Packages in SQL Server Management Studio (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="82634-103">이 항목에서는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 관리하는 Windows 서비스인 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="82634-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="82634-104">는 이전 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]버전과의 호환성을 위한 서비스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="82634-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="82634-105">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]부터는 Integration Services 서버의 패키지와 같은 개체를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82634-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="82634-106">이 절차에서는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 에 연결하고 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스에서 관리하는 패키지 목록을 보는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="82634-106">This procedure describes how to connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and view a list of the packages that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages.</span></span>  
  
### <a name="to-connect-to-integration-services"></a><span data-ttu-id="82634-107">Integration Services에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="82634-107">To connect to Integration Services</span></span>  
  
1.  <span data-ttu-id="82634-108">**시작**을 클릭하고 **모든 프로그램**, **Microsoft SQL Server**를 차례로 가리킨 다음 **SQL Server Management Studio**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82634-108">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="82634-109">**서버에 연결** 대화 상자의 **서버 유형** 목록에서 **Integration Services** 를 선택하고 **서버 이름** 상자에 서버 이름을 지정한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82634-109">In the **Connect to Server** dialog box, select **Integration Services** in the **Server type** list, provide a server name in the **Server name** box, and then click **Connect**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="82634-110">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에 연결할 수 없으면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스가 실행되고 있지 않는 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82634-110">If you cannot connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is likely not running.</span></span> <span data-ttu-id="82634-111">이 서비스의 상태를 확인하려면 **시작**을 클릭하고 **모든 프로그램**, **Microsoft SQL Server**, **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82634-111">To learn the status of the service, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="82634-112">왼쪽 창에서 **SQL Server 서비스**를 클릭하고</span><span class="sxs-lookup"><span data-stu-id="82634-112">In the left pane, click **SQL Server Services**.</span></span> <span data-ttu-id="82634-113">오른쪽 창에서 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="82634-113">In the right pane, find the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="82634-114">서비스가 실행되지 않았으면 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="82634-114">Start the service if it is not already running.</span></span>  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="82634-115">가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="82634-115">opens.</span></span> <span data-ttu-id="82634-116">기본적으로 SQL Server Management Studio의 왼쪽 아래에는 개체 탐색기 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="82634-116">By default the Object Explorer window is open and positioned in the lower-left corner of the studio.</span></span> <span data-ttu-id="82634-117">개체 탐색기가 열려 있지 않으면 **보기** 메뉴에서 **개체 탐색기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82634-117">If Object Explorer is not open, click **Object Explorer** on the **View** menu.</span></span>  
  
### <a name="to-view-the-packages-that-integration-services-service-manages"></a><span data-ttu-id="82634-118">Integration Services 서비스에서 관리하는 패키지를 보려면</span><span class="sxs-lookup"><span data-stu-id="82634-118">To view the packages that Integration Services service manages</span></span>  
  
1.  <span data-ttu-id="82634-119">개체 탐색기에서 저장된 패키지 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="82634-119">In Object Explorer, expand the Stored Packages folder.</span></span>  
  
2.  <span data-ttu-id="82634-120">저장된 패키지 하위 폴더를 확장하여 패키지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82634-120">Expand the Stored Packages subfolders to show packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82634-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82634-121">See Also</span></span>  
 <span data-ttu-id="82634-122">[SSIS 서비스를 &#40;패키지 관리&#41;](service/package-management-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="82634-122">[Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md) </span></span>  
 [<span data-ttu-id="82634-123">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="82634-123">Use SQL Server Management Studio</span></span>](../database-engine/use-sql-server-management-studio.md)  
  
  
