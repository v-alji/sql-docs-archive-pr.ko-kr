---
title: SQL Server 2014에서 관리 도구 기능의 주요 변경 내용 Microsoft Docs
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3ff3fad8-b569-4516-bd58-5a3efeb537e2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0487b6ab0958e0b83d4e8e34be507b5b3211ac87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652376"
---
# <a name="breaking-changes-to-management-tools-features-in-sql-server-2014"></a><span data-ttu-id="f6651-102">SQL Server 2014에서 관리 도구 기능의 주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="f6651-102">Breaking Changes to Management Tools Features in SQL Server 2014</span></span>
  <span data-ttu-id="f6651-103">이 항목에서는 관리 도구 기능의 주요 변경 내용을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f6651-103">This topic describes breaking changes to management tools features.</span></span> <span data-ttu-id="f6651-104">이러한 변경 내용에 따라 이전 버전의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 기반을 둔 애플리케이션, 스크립트 또는 기능을 사용하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6651-104">These changes might break applications, scripts, or functionalities that are based on earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f6651-105">이러한 문제는 업그레이드할 때 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6651-105">You might encounter these issues when you upgrade.</span></span> <span data-ttu-id="f6651-106">자세한 내용은 [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6651-106">For more information, see [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).</span></span>  
  
## <a name="breaking-changes-in-sssql14"></a><span data-ttu-id="f6651-107">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]의 주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="f6651-107">Breaking Changes in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span></span>  
 <span data-ttu-id="f6651-108">향후 정보 제공 예정</span><span class="sxs-lookup"><span data-stu-id="f6651-108">Information to come later.</span></span>  
  
## <a name="breaking-changes-in-sssql11"></a><span data-ttu-id="f6651-109">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]의 주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="f6651-109">Breaking Changes in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span></span>  
  
### <a name="you-cannot-use-sssql11-management-tools-to-create-a-utility-control-point-on-a-sskilimanjaro-instance-of-sql-server"></a><span data-ttu-id="f6651-110">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 관리 도구를 사용하여 SQL Server의 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 인스턴스에 유틸리티 제어 지점을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6651-110">You cannot use [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Management Tools to create a utility control point on a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] instance of SQL Server</span></span>  
 <span data-ttu-id="f6651-111">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]의 인스턴스에 유틸리티 제어 지점을 만들려면 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 관리 도구를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="f6651-111">To create a utility control point on an instance of [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], use [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Management Tools.</span></span>  
  
### <a name="smo-has-been-reversioned-in-sssql11"></a><span data-ttu-id="f6651-112">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]에서 SMO의 버전 변경</span><span class="sxs-lookup"><span data-stu-id="f6651-112">SMO has been reversioned in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span></span>  
 <span data-ttu-id="f6651-113">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 또는 이전 버전의 SMO를 사용하여 개발된 코드를 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 에 대해 빌드하려면 약간의 수정이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6651-113">Code developed with SMO from [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] or earlier versions might not build against [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] without minor modifications.</span></span> <span data-ttu-id="f6651-114">자세한 내용은 [Backward Compatibility in SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6651-114">For more information, see [Backward Compatibility in SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md).</span></span>  

## <a name="breaking-changes-in-sql-server-2005"></a><a name="previous-versions"></a><span data-ttu-id="f6651-115">SQL Server 2005의 주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="f6651-115">Breaking Changes in SQL Server 2005</span></span>  

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a><span data-ttu-id="f6651-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f6651-116">See Also</span></span>  
 [<span data-ttu-id="f6651-117">이전 버전과의 호환성</span><span class="sxs-lookup"><span data-stu-id="f6651-117">Backward Compatibility</span></span>](../../2014/getting-started/backward-compatibility.md)  
 [<span data-ttu-id="f6651-118">SQL Server 2014에서 관리 도구 기능의 주요 변경 내용에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="f6651-118">More about Breaking Changes to Management Tools Features in SQL Server 2014</span></span>](breaking-changes-to-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)  
  
  
