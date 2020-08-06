---
title: 옵션 (SQL Server AlwaysOn, 대시보드 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Alwayson.Dashboard
ms.assetid: 4369b588-e982-4b57-80a1-beb2e879ce0b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bef7622b56aabb2c908337fef4d110a12dd5a9bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649181"
---
# <a name="options-sql-server-alwayson-dashboard-page"></a><span data-ttu-id="30287-102">옵션(SQL Server AlwaysOn, 대시보드 페이지)</span><span class="sxs-lookup"><span data-stu-id="30287-102">Options (SQL Server AlwaysOn, Dashboard Page)</span></span>
  <span data-ttu-id="30287-103">옵션 대화 상자의 **Alwayson 대시보드 SQL Server** 페이지 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] **Options** 를 사용 하 여 alwayson 대시보드를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30287-103">Use the **SQL Server AlwaysOn Dashboard** page of the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]**Options** dialog box to configure the AlwaysOn Dashboard.</span></span>  
  
 <span data-ttu-id="30287-104">**이 페이지에 액세스하려면**</span><span class="sxs-lookup"><span data-stu-id="30287-104">**To access this page:**</span></span>  
  
 <span data-ttu-id="30287-105">**도구** 메뉴에서 **옵션**을 클릭하고 **SQL Server AlwaysOn** 폴더를 확장한 다음 **대시보드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30287-105">On the **Tools** menu, click **Options**, expand the **SQL Server AlwaysOn** folder, and then click **Dashboard**.</span></span>  
  
## <a name="on-this-page"></a><span data-ttu-id="30287-106">이 페이지에서</span><span class="sxs-lookup"><span data-stu-id="30287-106">On This Page</span></span>  
 <span data-ttu-id="30287-107">**자동 새로 고침 설정**</span><span class="sxs-lookup"><span data-stu-id="30287-107">**Turn on automatic refresh.**</span></span>  
 <span data-ttu-id="30287-108">자동 새로 고침을 사용하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30287-108">Click to enable automatic refresh.</span></span> <span data-ttu-id="30287-109">옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="30287-109">The options are:</span></span>  
  
-   <span data-ttu-id="30287-110">**새로 고침 간격(초)** 필드에는 대시보드를 새로 고치는 초 수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="30287-110">The **Refresh interval (in seconds)** field displays the number of seconds at which the dashboard will refresh.</span></span> <span data-ttu-id="30287-111">기본값은 30입니다.</span><span class="sxs-lookup"><span data-stu-id="30287-111">The default value is 30.</span></span> <span data-ttu-id="30287-112">자동 새로 고침을 사용하는 경우 이 필드를 편집하여 새로 고침 간격을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30287-112">When automatic refresh is enabled, you can edit this field to change the refresh interval.</span></span>  
  
-   <span data-ttu-id="30287-113">**연결 다시 시도 횟수** 에는 대시보드가 모니터링하는 가용성 그룹의 가용성 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결하려고 시도하는 횟수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="30287-113">The **Number of connection retries** displays the number of times that the dashboard will attempt to connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts an availability replica for an availability group that the Dashboard is monitoring.</span></span> <span data-ttu-id="30287-114">기본값은 65535입니다.</span><span class="sxs-lookup"><span data-stu-id="30287-114">The default value is 65535.</span></span> <span data-ttu-id="30287-115">자동 새로 고침을 사용하는 경우 이 필드를 편집하여 연결 재시도 횟수를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30287-115">When automatic refresh is enabled, you can edit this field to change the number of connection retries.</span></span>  
  
 <span data-ttu-id="30287-116">**사용자 정의 AlwaysOn 정책 사용**</span><span class="sxs-lookup"><span data-stu-id="30287-116">**Enable your user-defined AlwaysOn policy.**</span></span>  
 <span data-ttu-id="30287-117">AlwaysOn 정책을 직접 정의한 경우 이 옵션을 클릭하여 정책을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="30287-117">If you have defined your own AlwaysOn policy, click this option to enable your policy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30287-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30287-118">See Also</span></span>  
 [<span data-ttu-id="30287-119">AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="30287-119">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
