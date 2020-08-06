---
title: 로그 전달 보고서 보기(SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- viewing log shipping reports
- displaying log shipping reports
- log shipping [SQL Server], monitoring
- log shipping [SQL Server], viewing reports
ms.assetid: 3b549f2f-3683-45e5-b8e8-8095276c41ab
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d6c372a9b1f9af9e5948732e3bfb9384362f545
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661295"
---
# <a name="view-the-log-shipping-report-sql-server-management-studio"></a><span data-ttu-id="fd932-102">로그 전달 보고서 보기(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="fd932-102">View the Log Shipping Report (SQL Server Management Studio)</span></span>
  <span data-ttu-id="fd932-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 트랜잭션 로그 전달 상태 보고서를 보는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-103">This topic explains how to view the Transaction Log Shipping Status report in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="fd932-104">모니터 서버, 주 서버 또는 보조 서버에서 상태 보고서를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-104">You can run a status report at a monitor server, primary server, or secondary server.</span></span> <span data-ttu-id="fd932-105">로그 전달 구성에 대해 가장 완전한 정보를 보려면 모니터 서버 인스턴스에서 보고서를 보십시오.</span><span class="sxs-lookup"><span data-stu-id="fd932-105">To see the  most complete information about your log shipping configuration, view the report at the monitor server instance.</span></span>  
  
 <span data-ttu-id="fd932-106">이 보고서에는 모든 로그 전달 작업의 상태가 표시됩니다. 상태는 연결된 서버 인스턴스에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-106">The report displays the status of any log shipping activity whose status is available from the server instance to which you are connected.</span></span> <span data-ttu-id="fd932-107">한 데이터베이스에 대해서는 모니터 서버 역할을 하고 다른 데이터베이스에 대해서는 보조 서버 역할을 하는 등 서버 인스턴스가 다양한 역할로 여러 가지 구성과 관련되어 있으면 각 역할과 연관된 모든 구성 정보가 결과에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-107">If that server instance is involved in multiple configurations in different roles (such as serving as a monitor for one database and a secondary for another database), the displayed results contain the information of every configuration from the perspective of each role.</span></span> <span data-ttu-id="fd932-108">저장 프로시저가 특정한 로그 전달 구성을 위해 모니터 서버 인스턴스에 연결할 수 있으면 보고서에 해당 구성의 추가 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-108">If the stored procedure can connect to the monitor server instance for a given log shipping configuration, the report displays additional status for that configuration.</span></span>  
  
 <span data-ttu-id="fd932-109">현재 서버 인스턴스에서 수행하는 각 역할에 대해 다음 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-109">For each role performed by the current server instance, you can view the following information:</span></span>  
  
|<span data-ttu-id="fd932-110">역할</span><span class="sxs-lookup"><span data-stu-id="fd932-110">Role</span></span>|<span data-ttu-id="fd932-111">표시되는 정보</span><span class="sxs-lookup"><span data-stu-id="fd932-111">Information displayed</span></span>|  
|----------|---------------------------|  
|<span data-ttu-id="fd932-112">모니터</span><span class="sxs-lookup"><span data-stu-id="fd932-112">Monitor</span></span>|<span data-ttu-id="fd932-113">이 서버 인스턴스를 모니터 서버로 사용하는 모든 주 서버 및 보조 서버의 이름과 상태</span><span class="sxs-lookup"><span data-stu-id="fd932-113">The name and status of every primary server and secondary server that uses this server instance as its monitor server.</span></span>|  
|<span data-ttu-id="fd932-114">주</span><span class="sxs-lookup"><span data-stu-id="fd932-114">Primary</span></span>|<span data-ttu-id="fd932-115">주 데이터베이스 각각에 대한 주 데이터베이스 이름 및 주 서버로서 현재 서버 인스턴스의 상태와 이름.</span><span class="sxs-lookup"><span data-stu-id="fd932-115">For each primary database, the status and name of the current server instance (as the primary server), along with the primary database name.</span></span> <span data-ttu-id="fd932-116">보고서에는 주 서버에 로컬로 저장되어 있는 백업 작업의 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-116">The report displays the status of the backup job (which is stored locally on the primary server).</span></span><br /><br /> <span data-ttu-id="fd932-117">보고서에는 해당되는 각 보조 서버에 대한 행도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-117">The report also contains a row for each of the corresponding secondary servers.</span></span> <span data-ttu-id="fd932-118">구성에서 모니터 서버를 사용하고 저장 프로시저가 모니터에 연결할 수 있으면 이러한 행에 최신 로그 백업의 복사 상태 및 복원 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-118">If the configuration uses a monitor server and the stored procedure can connect to the monitor, these rows display the copy status and restore status for the most recent log backup.</span></span>|  
|<span data-ttu-id="fd932-119">보조</span><span class="sxs-lookup"><span data-stu-id="fd932-119">Secondary</span></span>|<span data-ttu-id="fd932-120">보조 데이터베이스 각각에 대한 보조 데이터베이스 이름 및 보조 서버로서 현재 서버 인스턴스의 상태와 이름</span><span class="sxs-lookup"><span data-stu-id="fd932-120">For each secondary database, the status and name of the current server instance (as the secondary server), along with the secondary database name.</span></span><br /><br /> <span data-ttu-id="fd932-121">보고서에는 보조 서버에서 수행되는 복사 및 복원 작업의 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-121">The report displays the status of the copy and restore jobs at the secondary server.</span></span><br /><br /> <span data-ttu-id="fd932-122">보고서에는 해당되는 주 서버에 대한 행도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-122">The report also contains a row for the corresponding primary server.</span></span> <span data-ttu-id="fd932-123">구성에서 모니터 서버를 사용하고 저장 프로시저가 모니터에 연결할 수 있으면 이 행에 최신 로그 백업의 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-123">If the configuration uses a monitor server and the stored procedure can connect to the monitor, this row displays the status of the most recent log backup.</span></span>|  
  
 <span data-ttu-id="fd932-124">표시되는 정보는 서버 인스턴스가 모니터 서버인지, 주 서버인지 또는 보조 서버인지에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-124">The information displayed depends on whether the server instance is a monitor server, primary server, or secondary server.</span></span> <span data-ttu-id="fd932-125">정보를 사용할 수 없으면 해당 셀이 회색으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-125">If information is not available, the corresponding cells are grayed out.</span></span>  
  
 <span data-ttu-id="fd932-126">보고서는 **sp_help_log_shipping_monitor**를 호출하여 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-126">The report calls **sp_help_log_shipping_monitor** to get the data.</span></span> <span data-ttu-id="fd932-127">필요한 권한에 대한 자세한 내용은 [sp_help_log_shipping_monitor&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd932-127">For information about the required permissions, see [sp_help_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-transact-sql).</span></span>  
  
### <a name="to-display-the-transaction-log-shipping-status-report-on-a-server-instance"></a><span data-ttu-id="fd932-128">서버 인스턴스의 트랜잭션 로그 전달 상태 보고서를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="fd932-128">To display the Transaction Log Shipping Status report on a server instance</span></span>  
  
1.  <span data-ttu-id="fd932-129">모니터 서버, 주 서버 또는 보조 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-129">Connect to a monitor server, primary server, or secondary server.</span></span>  
  
2.  <span data-ttu-id="fd932-130">개체 탐색기에서 서버 인스턴스를 마우스 오른쪽 단추로 클릭하고 **보고서**를 가리킨 후 **표준 보고서**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-130">Right-click the server instance in Object Explorer, point to **Reports**, and point to **Standard Reports**.</span></span>  
  
3.  <span data-ttu-id="fd932-131">**트랜잭션 로그 전달 상태**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd932-131">Click **Transaction Log Shipping Status**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd932-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd932-132">See Also</span></span>  
 [<span data-ttu-id="fd932-133">로그 전달 모니터링&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="fd932-133">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
  
