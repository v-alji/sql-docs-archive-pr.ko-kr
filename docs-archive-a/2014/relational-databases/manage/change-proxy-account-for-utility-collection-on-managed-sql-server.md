---
title: SQL Server (SQL Server 유틸리티) Managed Instance에서 유틸리티 컬렉션 집합에 대 한 프록시 계정을 변경 합니다. Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19f60c607ed661ef42c1c1c0e48854cdfd69a912
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647690"
---
# <a name="change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server-sql-server-utility"></a><span data-ttu-id="b01aa-102">SQL Server 관리되는 인스턴스의 유틸리티 컬렉션 집합을 위한 프록시 계정 변경(SQL Server 유틸리티)</span><span class="sxs-lookup"><span data-stu-id="b01aa-102">Change the Proxy Account for the Utility Collection Set on a Managed Instance of SQL Server (SQL Server Utility)</span></span>
  <span data-ttu-id="b01aa-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 관리되는 인스턴스의 유틸리티 컬렉션 집합에 대한 프록시 계정을 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b01aa-103">This topic describes how to change the proxy account for the Utility Collection Set on a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b01aa-104">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b01aa-104">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server"></a><span data-ttu-id="b01aa-105">SQL Server의 관리되는 인스턴스에서 유틸리티 컬렉션 집합에 대한 프록시 계정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="b01aa-105">To change the proxy account for the utility collection set on a managed instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="b01aa-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b01aa-106">Remove the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
    -   <span data-ttu-id="b01aa-107">SSMS의 **유틸리티 탐색기**에서 **관리되는 인스턴스** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b01aa-107">In **Utility Explorer** in SSMS, click on the **Managed Instances** node.</span></span>  
  
    -   <span data-ttu-id="b01aa-108">**유틸리티 탐색기** 목록 뷰에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 이름을 마우스 오른쪽 단추로 클릭하고 **Managed Instance 제거...** 를 선택합니다. 자세한 내용은 [SQL Server 유틸리티에서 SQL Server 인스턴스 제거](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b01aa-108">In the **Utility Explorer** list view, right-click the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name, and select **Remove Managed Instance...**. For more information, see [Remove an Instance of SQL Server from the SQL Server Utility](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).</span></span>  
  
2.  <span data-ttu-id="b01aa-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 다시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="b01aa-109">Enroll the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility again.</span></span>  
  
    -   <span data-ttu-id="b01aa-110">SSMS의 **유틸리티 탐색기**에서 **Managed Instance** 노드를 마우스 오른쪽 단추로 클릭하고 **Managed Instance 추가...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b01aa-110">In **Utility Explorer** in SSMS, right-click on the **Managed Instances** node, and select **Add Managed Instance...**.</span></span>  
  
    -   <span data-ttu-id="b01aa-111">표시되는 메시지에 따라 마법사를 완료하여 새 프록시 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b01aa-111">Follow prompts to complete the wizard, specifying the new proxy account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b01aa-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b01aa-112">See Also</span></span>  
 <span data-ttu-id="b01aa-113">[SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="b01aa-113">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="b01aa-114">SQL Server 유틸리티 문제 해결</span><span class="sxs-lookup"><span data-stu-id="b01aa-114">Troubleshoot the SQL Server Utility</span></span>](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
