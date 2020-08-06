---
title: SQL Server 인스턴스의 자동 시작 방지 (SQL Server 구성 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, stopping
- SQL Server, automatic startup
- canceling automatic startup
- stopping SQL Server
- preventing automatic startups [SQL Server]
ms.assetid: 782663cf-f3d7-4cc6-b621-21e4550f0322
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8f93f5abc749f589ab4208b3a4c9434ca63b8769
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651896"
---
# <a name="prevent-automatic-startup-of-an-instance-of-sql-server-sql-server-configuration-manager"></a><span data-ttu-id="6a725-102">SQL Server 인스턴스의 자동 시작 방지(SQL Server 구성 관리자)</span><span class="sxs-lookup"><span data-stu-id="6a725-102">Prevent Automatic Startup of an Instance of SQL Server (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="6a725-103">이 항목에서는 SQL Server 구성 관리자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 인스턴스가 자동으로 시작되지 않도록 방지하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6a725-103">This topic describes how prevent an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from starting automatically in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6a725-104">는 일반적으로 자동으로 시작되도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a725-104">is normally configured to start automatically.</span></span> <span data-ttu-id="6a725-105">인스턴스의 시작 모드를 수동으로 설정하면 이러한 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a725-105">You can change that by setting the start mode for the instance to manual.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6a725-106">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="6a725-106">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-prevent-automatic-startup-of-an-instance-of-sql-server"></a><span data-ttu-id="6a725-107">SQL Server 인스턴스의 자동 시작을 방지하려면</span><span class="sxs-lookup"><span data-stu-id="6a725-107">To prevent automatic startup of an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="6a725-108">**시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6a725-108">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="6a725-109">SQL Server 구성 관리자에서 **서비스**를 확장한 다음 **SQL Server**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6a725-109">In SQL Server Configuration Manager, expand **Services**, and then click **SQL Server**.</span></span>  
  
3.  <span data-ttu-id="6a725-110">세부 정보 창에서 **MSSQLServer**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6a725-110">In the details pane, right-click **MSSQLServer**, and then click **Properties.**</span></span>  
  
4.  <span data-ttu-id="6a725-111">**SQL Server \<**_instancename_**> 속성** 대화 상자의 **속성** 상자에서 **시작 모드** 의 값을 **수동**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a725-111">In the **SQL Server \<**_instancename_**> Properties** dialog box, in the **Properties** box, set the value of **Start Mode** to **Manual**.</span></span>  
  
5.  <span data-ttu-id="6a725-112">**확인**을 클릭하여 **SQL Server \<**_instancename_**> 속성** 대화 상자를 닫은 다음, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="6a725-112">Click **OK** to close the **SQL Server \<**_instancename_**> Properties** dialog box, and then close [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a725-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a725-113">See Also</span></span>  
 [<span data-ttu-id="6a725-114">데이터베이스 엔진, SQL Server 에이전트 또는 SQL Server Browser 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="6a725-114">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
