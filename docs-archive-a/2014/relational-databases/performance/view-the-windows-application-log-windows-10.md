---
title: Windows 애플리케이션 로그 보기(Windows) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- application logs [SQL Server]
- logs [SQL Server], application
- monitoring Windows NT application log [SQL Server]
- Windows NT application logs [SQL Server]
- displaying logs
- monitoring [SQL Server], events
- logs [SQL Server], viewing
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1255e95833d9fc56abd1700f5acb0d2f49ebf77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731548"
---
# <a name="view-the-windows-application-log-windows"></a><span data-ttu-id="ca6f6-102">Windows 애플리케이션 로그 보기(Windows)</span><span class="sxs-lookup"><span data-stu-id="ca6f6-102">View the Windows Application Log (Windows)</span></span>
  <span data-ttu-id="ca6f6-103">Windows 애플리케이션 로그를 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 구성한 경우 각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 세션에서는 해당 로그에 새 이벤트를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="ca6f6-103">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to use the Windows application log, each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session writes new events to that log.</span></span> <span data-ttu-id="ca6f6-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그와는 달리 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 시작할 때마다 새 애플리케이션 로그가 생성되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca6f6-104">Unlike the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, a new application log is not created each time you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-view-the-windows-application-log"></a><span data-ttu-id="ca6f6-105">Windows 애플리케이션 로그를 보려면</span><span class="sxs-lookup"><span data-stu-id="ca6f6-105">To view the Windows application log</span></span>  
  
1.  <span data-ttu-id="ca6f6-106">**시작** 메뉴에서 **모든 프로그램**, **관리 도구**를 차례로 가리킨 다음 **이벤트 뷰어**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ca6f6-106">On the **Start** menu, point to **All Programs**, point to **Administrative Tools**, and then click **Event Viewer**.</span></span>  
  
2.  <span data-ttu-id="ca6f6-107">이벤트 뷰어에서 **애플리케이션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ca6f6-107">In Event Viewer, click **Application**.</span></span>  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="ca6f6-108">이벤트는 **원본** 열에서 **MSSQLSERVER** 항목으로 식별됩니다(명명된 인스턴스는 **MSSQL$** _<instance_name>_ 으로 식별됨).</span><span class="sxs-lookup"><span data-stu-id="ca6f6-108">events are identified by the entry **MSSQLSERVER** (named instances are identified with **MSSQL$**_<instance_name>_) in the **Source** column.</span></span> <span data-ttu-id="ca6f6-109">SQL Server 에이전트 이벤트는 SQLSERVERAGENT 항목으로 식별됩니다. 명명된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 이벤트는 **SQLAgent$** \<*instance_name*>으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca6f6-109">SQL Server Agent events are identified by the entry SQLSERVERAGENT (for named instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events are identified with **SQLAgent$**\<*instance_name*>).</span></span> <span data-ttu-id="ca6f6-110">Microsoft Search 서비스 이벤트는 **Microsoft Search**항목으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca6f6-110">Microsoft Search service events are identified by the entry **Microsoft Search**.</span></span>  
  
4.  <span data-ttu-id="ca6f6-111">다른 컴퓨터의 로그를 보려면 **이벤트 뷰어**를 마우스 오른쪽 단추로 클릭 하 고 **다른 컴퓨터에 연결을** 클릭 한 다음 **컴퓨터 선택**대화 상자를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca6f6-111">To view the log of a different computer, right-click **Event Viewer**, click **Connect to another computer,** and complete the **Select Computer**dialog box.</span></span>  
  
5.  <span data-ttu-id="ca6f6-112">선택적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이벤트만 표시하려면 **보기** 메뉴에서 **필터**를 클릭한 후 **이벤트 원본** 목록에서 **MSSQLSERVER**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ca6f6-112">Optionally, to display only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events, on the **View** menu click **Filter**, and in the **Event source** list, select **MSSQLSERVER**.</span></span> <span data-ttu-id="ca6f6-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 이벤트만 표시하려면 **이벤트 원본** 목록에서 **SQLSERVERAGENT** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ca6f6-113">To view only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events, instead select **SQLSERVERAGENT** in the **Event source** list.</span></span>  
  
6.  <span data-ttu-id="ca6f6-114">이벤트에 대한 자세한 내용을 보려면 해당 이벤트를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ca6f6-114">To view more information about an event, double-click the event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca6f6-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca6f6-115">See Also</span></span>  
 [<span data-ttu-id="ca6f6-116">SQL Server 오류 로그 보기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ca6f6-116">View the SQL Server Error Log &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
  
