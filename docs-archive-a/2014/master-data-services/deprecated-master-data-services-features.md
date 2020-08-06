---
title: SQL Server 2014에서 사용 되지 않는 MDS(Master Data Services) 기능 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce532e9f407ec475f7e59c0d79659265a9e0bf3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728408"
---
# <a name="deprecated-master-data-services-features-in-sql-server-2014"></a><span data-ttu-id="fb088-102">SQL Server 2014에서 사용되지 않는 MDS(Master Data Services) 기능</span><span class="sxs-lookup"><span data-stu-id="fb088-102">Deprecated Master Data Services Features in SQL Server 2014</span></span>
  <span data-ttu-id="fb088-103">이 항목에서는 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 에서 계속 제공되지만 더 이상 사용되지 않는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fb088-103">This topic describes the deprecated [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] features that are still available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="fb088-104">이러한 기능은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 이후 릴리스에서 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="fb088-104">These features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fb088-105">새 애플리케이션에는 이러한 기능을 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb088-105">Deprecated features should not be used in new applications.</span></span>  
  
## <a name="staging-process"></a><span data-ttu-id="fb088-106">준비 프로세스</span><span class="sxs-lookup"><span data-stu-id="fb088-106">Staging Process</span></span>  
 <span data-ttu-id="fb088-107">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 에서 사용된 준비 프로세스는 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에서 더 이상 사용되지 않습니다. 하지만 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서는 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb088-107">The staging process that was used in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] is no longer available in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application; however it is still available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="fb088-108">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 준비 프로세스의 준비 오류는 더 이상 UI에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb088-108">Staging errors from the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] staging process are no longer displayed in the UI.</span></span> <span data-ttu-id="fb088-109">준비 프로세스 중에 채워지는 오류 코드는 준비 테이블에서 계속 사용할 수 있으며에서 찾을 수 있습니다 [https://msdn.microsoft.com/library/ff487022.aspx](https://msdn.microsoft.com/library/ff487022.aspx) .</span><span class="sxs-lookup"><span data-stu-id="fb088-109">Error codes that are populated during the staging process are still available in the staging tables, and can be found here: [https://msdn.microsoft.com/library/ff487022.aspx](https://msdn.microsoft.com/library/ff487022.aspx).</span></span>  
  
 <span data-ttu-id="fb088-110">준비 테이블(tblStgMember, tblStgMemberAttribute 및 tblStgRelationship)은 여전히 데이터베이스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb088-110">The staging tables (tblStgMember, tblStgMemberAttribute, and tblStgRelationship) are still available in the database.</span></span> <span data-ttu-id="fb088-111">준비 프로세스를 시작하는 데 사용되는 저장 프로시저(mdm.udpStagingSweep)는 여전히 데이터베이스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb088-111">The stored procedure used to initiate the staging process (mdm.udpStagingSweep) is still available in the database.</span></span>  
  
 <span data-ttu-id="fb088-112">준비 프로세스를 호출하는 웹 서비스 메서드를 여전히 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb088-112">The web service methods that call the staging process are still available.</span></span>  
  
 <span data-ttu-id="fb088-113">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에서 설정된 준비 간격이 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 및 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]의 준비 프로세스에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb088-113">The staging interval set in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] applies to the staging process in both [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] and [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="fb088-114">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]에는 향상된 성능의 새로운 준비 프로세스가 구현되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fb088-114">A new, higher performance staging process has been implemented in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="fb088-115">자세한 내용은 [데이터 가져오기&#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb088-115">For more information, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
## <a name="metadata"></a><span data-ttu-id="fb088-116">메타데이터</span><span class="sxs-lookup"><span data-stu-id="fb088-116">Metadata</span></span>  
 <span data-ttu-id="fb088-117">메타데이터 모델은 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에 계속 표시되지만 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb088-117">Though the Metadata model is still displayed in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, it should not be used.</span></span> <span data-ttu-id="fb088-118">후속 릴리스에서 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="fb088-118">It will be removed in a future release.</span></span> <span data-ttu-id="fb088-119">사용자는 **탐색기** 기능 영역에서 더 이상 메타데이터를 볼 수 없으며 더 이상 메타데이터 모델 버전을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fb088-119">Users can also no longer view metadata in the **Explorer** functional area, and you can no longer create versions of the Metadata model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb088-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb088-120">See Also</span></span>  
 [<span data-ttu-id="fb088-121">SQL Server 2014에서 지원되지 않는 MDS(Master Data Services) 기능</span><span class="sxs-lookup"><span data-stu-id="fb088-121">Discontinued Master Data Services Features in SQL Server 2014</span></span>](discontinued-master-data-services-features.md)  
  
  
