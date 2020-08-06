---
title: 마스터 서버에서 여러 대상 서버 제거 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
author: stevestein
ms.author: sstein
ms.openlocfilehash: b31a8bc38968733de0a23f67a71772721c8baedd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731356"
---
# <a name="defect-multiple-target-servers-from-a-master-server"></a><span data-ttu-id="012fe-102">Defect Multiple Target Servers from a Master Server</span><span class="sxs-lookup"><span data-stu-id="012fe-102">Defect Multiple Target Servers from a Master Server</span></span>
  <span data-ttu-id="012fe-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 다중 서버 관리 구성에서 여러 대상 서버를 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="012fe-103">This topic describes how to defect multiple target servers from a multiserver administration configuration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="012fe-104">이 절차는 마스터 서버에서 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="012fe-104">Run this procedure from the master server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="012fe-105">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="012fe-105">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a><span data-ttu-id="012fe-106">마스터 서버에서 다중 대상 서버를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="012fe-106">To defect multiple target servers from a master server</span></span>  
  
1.  <span data-ttu-id="012fe-107">**개체 탐색기**에서 마스터 서버로 구성된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="012fe-107">In **Object Explorer**, expand a server that is configured as a master server.</span></span>  
  
2.  <span data-ttu-id="012fe-108">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭하고 **다중 서버 관리**를 가리킨 다음 **대상 서버 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="012fe-108">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="012fe-109">**명령 게시**를 클릭하고 **명령 유형** 목록에서 **제거**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="012fe-109">Click **Post Instructions**, and then in the **Instruction type** list, select **Defect**.</span></span>  
  
4.  <span data-ttu-id="012fe-110">**받는 사람**에서 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="012fe-110">Under **Recipients**, do one of the following:</span></span>  
  
    -   <span data-ttu-id="012fe-111">이 마스터 서버의 모든 대상 서버를 제거하려면 **모든 대상 서버** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="012fe-111">Click **All target servers** to defect all target servers of this master server.</span></span> <span data-ttu-id="012fe-112">현재 다중 서버 관리 구성을 완전히 제거하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="012fe-112">Use this option if you want to completely uninstall the current multiserver administration configuration.</span></span>  
  
    -   <span data-ttu-id="012fe-113">이 마스터 서버의 모든 대상 서버가 아닌 일부 대상 서버를 제거하려면 **대상 서버 지정**을 클릭한 다음 해당 **선택** 상자를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="012fe-113">Click **These target servers**, and then click the corresponding **Select** box, to defect some, but not all, target servers of this master server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="012fe-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="012fe-114">See Also</span></span>  
 <span data-ttu-id="012fe-115">[다중 서버 환경 만들기](create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="012fe-115">[Create a Multiserver Environment](create-a-multiserver-environment.md) </span></span>  
 <span data-ttu-id="012fe-116">[기업 내 관리 자동화](automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="012fe-116">[Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md) </span></span>  
 [<span data-ttu-id="012fe-117">Defect a Target Server from a Master Server</span><span class="sxs-lookup"><span data-stu-id="012fe-117">Defect a Target Server from a Master Server</span></span>](defect-a-target-server-from-a-master-server.md)  
  
  
