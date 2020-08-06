---
title: network packet size 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default packet size
- size [SQL Server], packets
- packets [SQL Server], size
- network packet size option
ms.assetid: 236985bf-fc4a-4a57-98f7-a71ef977fd7b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69e5963675349bceff6a0ee022f6dc28da03db59
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732015"
---
# <a name="configure-the-network-packet-size-server-configuration-option"></a><span data-ttu-id="9f397-102">network packet size 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="9f397-102">Configure the network packet size Server Configuration Option</span></span>
  <span data-ttu-id="9f397-103">이 항목에서는 또는을 사용 하 `network packet size` 여에서 서버 구성 옵션을 구성 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9f397-103">This topic describes how to configure the `network packet size` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="9f397-104">`network packet size`옵션은 전체 네트워크에서 사용 되는 패킷 크기 (바이트)를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-104">The `network packet size` option sets the packet size (in bytes) that is used across the whole network.</span></span> <span data-ttu-id="9f397-105">패킷은 클라이언트와 서버 간에 요청 및 결과를 전송하는 고정된 크기의 데이터 청크입니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-105">Packets are the fixed-size chunks of data that transfer requests and results between clients and servers.</span></span> <span data-ttu-id="9f397-106">기본 패킷 크기는 4,096바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-106">The default packet size is 4,096 bytes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f397-107">성능이 향상될 것이라는 확신이 없으면 패킷 크기를 변경하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="9f397-107">Do not change the packet size unless you are certain that it will improve performance.</span></span> <span data-ttu-id="9f397-108">대부분의 애플리케이션에는 기본 패킷 크기가 제일 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-108">For most applications, the default packet size is best.</span></span>  
  
 <span data-ttu-id="9f397-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="9f397-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9f397-110">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="9f397-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9f397-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="9f397-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9f397-112">권장 사항</span><span class="sxs-lookup"><span data-stu-id="9f397-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="9f397-113">보안</span><span class="sxs-lookup"><span data-stu-id="9f397-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9f397-114">**네트워크 패킷 크기 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="9f397-114">**To configure the network packet size option, using:**</span></span>  
  
     [<span data-ttu-id="9f397-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9f397-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9f397-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9f397-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="9f397-117">**후속 작업:**  [네트워크 패킷 크기 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="9f397-117">**Follow Up:**  [After you configure the network packet size option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9f397-118">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="9f397-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9f397-119">제한 사항</span><span class="sxs-lookup"><span data-stu-id="9f397-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="9f397-120">암호화된 연결의 최대 network packet size는 16,383바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-120">The maximum network packet size for encrypted connections is 16,383 bytes.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="9f397-121">권장 사항</span><span class="sxs-lookup"><span data-stu-id="9f397-121">Recommendations</span></span>  
  
-   <span data-ttu-id="9f397-122">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-122">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="9f397-123">애플리케이션에서 대량 복사 작업을 수행하거나 많은 양의 텍스트 또는 이미지 데이터를 주고받을 때 패킷 크기를 기본값보다 크게 설정하면 네트워크에서 읽기 및 쓰기 작업의 양이 줄어들므로 효율성이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-123">If an application does bulk copy operations or sends or receives large amounts of text or image data, a packet size larger than the default might improve efficiency because it results in fewer network read-and-write operations.</span></span> <span data-ttu-id="9f397-124">애플리케이션이 적은 양의 정보를 보내거나 받을 경우 대부분의 데이터를 전송할 수 있도록 패킷 크기를 512바이트로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-124">If an application sends and receives small amounts of information, the packet size can be set to 512 bytes, which is sufficient for most data transfers.</span></span>  
  
-   <span data-ttu-id="9f397-125">서로 다른 네트워크 프로토콜을 사용하는 시스템에서는 네트워크 패킷 크기를 가장 일반적으로 사용되는 프로토콜 크기로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-125">On systems that are using different network protocols, set network packet size to the size for the most common protocol used.</span></span> <span data-ttu-id="9f397-126">network packet size 옵션은 네트워크 프로토콜이 보다 큰 패킷을 지원할 때 네트워크 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-126">The network packet size option improves network performance when network protocols support larger packets.</span></span> <span data-ttu-id="9f397-127">클라이언트 애플리케이션에서 이 값을 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-127">Client applications can override this value.</span></span>  
  
-   <span data-ttu-id="9f397-128">OLE DB, ODBC(Open Database Connectivity) 및 DB-Library 함수를 호출하여 패킷 크기 변경을 요청할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-128">You can also call OLE DB, Open Database Connectivity (ODBC), and DB-Library functions request a change the packet size.</span></span> <span data-ttu-id="9f397-129">서버에서 요청된 패킷 크기가 지원되지 않으면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 클라이언트에게 경고 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-129">If the server cannot support the requested packet size, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] will send a warning message to the client.</span></span> <span data-ttu-id="9f397-130">일부 환경에서는 패킷 크기를 변경할 경우 다음 오류가 발생하면서 통신 연결이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-130">In some circumstances, changing the packet size might lead to a communication link failure, such as the following:</span></span>  
  
     `Native Error: 233, no process is on the other end of the pipe.`  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9f397-131">보안</span><span class="sxs-lookup"><span data-stu-id="9f397-131">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9f397-132">권한</span><span class="sxs-lookup"><span data-stu-id="9f397-132">Permissions</span></span>  
 <span data-ttu-id="9f397-133">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-133">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="9f397-134">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-134">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="9f397-135">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-135">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9f397-136">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="9f397-136">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-network-packet-size-option"></a><span data-ttu-id="9f397-137">네트워크 패킷 크기 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="9f397-137">To configure the network packet size option</span></span>  
  
1.  <span data-ttu-id="9f397-138">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-138">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="9f397-139">**고급** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-139">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="9f397-140">**네트워크**에서 **네트워크 패킷 크기** 상자의 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-140">Under **Network**, select a value for the **Network Packet Size** box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9f397-141">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="9f397-141">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-network-packet-size-option"></a><span data-ttu-id="9f397-142">네트워크 패킷 크기 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="9f397-142">To configure the network packet size option</span></span>  
  
1.  <span data-ttu-id="9f397-143">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-143">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9f397-144">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-144">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9f397-145">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9f397-146">다음 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `network packet size` 옵션의 값을 `6500` 바이트로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-146">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `network packet size` option to `6500` bytes.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'network packet size', 6500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="9f397-147">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-147">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-network-packet-size-option"></a><a name="FollowUp"></a> <span data-ttu-id="9f397-148">후속 작업: 네트워크 패킷 크기 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="9f397-148">Follow Up: After you configure the network packet size option</span></span>  
 <span data-ttu-id="9f397-149">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f397-149">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f397-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9f397-150">See Also</span></span>  
 <span data-ttu-id="9f397-151">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9f397-151">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="9f397-152">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9f397-152">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="9f397-153">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9f397-153">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
