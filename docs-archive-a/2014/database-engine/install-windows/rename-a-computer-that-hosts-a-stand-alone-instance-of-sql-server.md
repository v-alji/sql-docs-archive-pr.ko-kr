---
title: SQL Server의 독립 실행형 인스턴스를 호스팅하는 컴퓨터 이름 바꾸기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- remote login errors [SQL Server]
- standalone computer names [SQL Server]
- names [SQL Server], standalone instances of SQL Server
- renaming standalone instances of SQL Server
- sysservers system table
- removing remote logins
- deleting remote logins
- dropping remote logins
ms.assetid: bbaf1445-b8a2-4ebf-babe-17d8cf20b037
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 079348921900a7cbf880027433280253df1a9e30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740287"
---
# <a name="rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server"></a><span data-ttu-id="6f6a5-102">SQL Server의 독립 실행형 인스턴스를 호스팅하는 컴퓨터 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="6f6a5-102">Rename a Computer that Hosts a Stand-Alone Instance of SQL Server</span></span>
  <span data-ttu-id="6f6a5-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하는 컴퓨터의 이름을 변경하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시작 시 새 이름이 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-103">When you change the name of the computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the new name is recognized during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup.</span></span> <span data-ttu-id="6f6a5-104">컴퓨터 이름을 다시 설정하기 위해 설치 프로그램을 다시 실행할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-104">You do not have to run Setup again to reset the computer name.</span></span> <span data-ttu-id="6f6a5-105">대신 다음 단계를 사용하여 sys.servers에 저장되고 @@SERVERNAME 시스템 함수로 보고되는 시스템 메타데이터를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-105">Instead, use the following steps to update system metadata that is stored in sys.servers and reported by the system function @@SERVERNAME.</span></span> <span data-ttu-id="6f6a5-106">@@SERVERNAME을 사용하거나 sys.servers에서 서버 이름을 쿼리하는 애플리케이션 및 원격 연결에 대해 변경된 컴퓨터 이름을 반영하도록 시스템 메타데이터를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-106">Update system metadata to reflect computer name changes for remote connections and applications that use @@SERVERNAME, or that query the server name from sys.servers.</span></span>  
  
 <span data-ttu-id="6f6a5-107">다음 단계는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 이름 변경 작업에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-107">The following steps cannot be used to rename an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6f6a5-108">이 단계는 인스턴스 이름에서 컴퓨터 이름에 해당하는 부분을 변경하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-108">They can be used only to rename the part of the instance name that corresponds to the computer name.</span></span> <span data-ttu-id="6f6a5-109">예를 들어 Instance1이라는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 호스팅하는 MB1이라는 컴퓨터의 이름을 다른 이름(예: MB2)으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-109">For example, you can change a computer named MB1 that hosts an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] named Instance1 to another name, such as MB2.</span></span> <span data-ttu-id="6f6a5-110">그러나 이름에서 인스턴스에 해당하는 Instance1은 변경되지 않고 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-110">However, the instance part of the name, Instance1, will remain unchanged.</span></span> <span data-ttu-id="6f6a5-111">이 예제의 경우 \\\\*ComputerName*\\*InstanceName* 은 \\\MB1\Instance1에서 \\\MB2\Instance1로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-111">In this example, the \\\\*ComputerName*\\*InstanceName* would be changed from \\\MB1\Instance1 to \\\MB2\Instance1.</span></span>  
  
 <span data-ttu-id="6f6a5-112">**시작하기 전 주의 사항**</span><span class="sxs-lookup"><span data-stu-id="6f6a5-112">**Before you begin**</span></span>  
  
 <span data-ttu-id="6f6a5-113">이름 바꾸기 프로세스를 시작하기 전에 다음 정보를 검토하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-113">Before you begin the renaming process, review the following information:</span></span>  
  
-   <span data-ttu-id="6f6a5-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터의 일부인 경우 컴퓨터의 이름을 바꾸는 프로세스는 독립 실행형 인스턴스를 호스팅하는 컴퓨터의 이름을 바꾸는 프로세스와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-114">When an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is part of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, the computer renaming process differs from a computer that hosts a stand-alone instance.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6f6a5-115">는 복제와 함께 로그 전달을 사용하는 경우를 제외하고 복제에 관련된 컴퓨터의 이름 바꾸기를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-115">does not support renaming computers that are involved in replication, except when you use log shipping with replication.</span></span> <span data-ttu-id="6f6a5-116">주 컴퓨터가 영구적으로 손실되면 로그 전달의 보조 컴퓨터 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-116">The secondary computer in log shipping can be renamed if the primary computer is permanently lost.</span></span> <span data-ttu-id="6f6a5-117">자세한 내용은 [로그 전달 및 복제&#40;SQL Server&#41;](../log-shipping/log-shipping-and-replication-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-117">For more information, see [Log Shipping and Replication &#40;SQL Server&#41;](../log-shipping/log-shipping-and-replication-sql-server.md).</span></span>  
  
-   <span data-ttu-id="6f6a5-118">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 사용하도록 구성된 컴퓨터의 이름을 바꾸면 컴퓨터 이름이 변경된 후 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]를 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-118">When you rename a computer that is configured to use [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] might not be available after the computer name change.</span></span> <span data-ttu-id="6f6a5-119">자세한 내용은 [보고서 서버 컴퓨터 이름 바꾸기](../../reporting-services/report-server/rename-a-report-server-computer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-119">For more information, see [Rename a Report Server Computer](../../reporting-services/report-server/rename-a-report-server-computer.md).</span></span>  
  
-   <span data-ttu-id="6f6a5-120">데이터베이스 미러링을 사용하도록 구성된 컴퓨터의 이름을 바꾸는 경우 이름 바꾸기 작업을 수행하기 전에 데이터베이스 미러링을 해제한 다음</span><span class="sxs-lookup"><span data-stu-id="6f6a5-120">When you rename a computer that is configured to use database mirroring, you must turn off database mirroring before the renaming operation.</span></span> <span data-ttu-id="6f6a5-121">데이터베이스 미러링을 새 컴퓨터 이름으로 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-121">Then, re-establish database mirroring with the new computer name.</span></span> <span data-ttu-id="6f6a5-122">데이터베이스 미러링의 메타데이터는 새로운 컴퓨터 이름을 반영하도록 자동으로 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-122">Metadata for database mirroring will not be updated automatically to reflect the new computer name.</span></span> <span data-ttu-id="6f6a5-123">다음 단계에 따라 시스템 메타데이터를 업데이트하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-123">Use the following steps to update system metadata.</span></span>  
  
-   <span data-ttu-id="6f6a5-124">컴퓨터 이름에 대해 하드 코딩된 참조를 사용하는 Windows 그룹을 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결하는 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-124">Users who connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through a Windows group that uses a hard-coded reference to the computer name might not be able to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6f6a5-125">이는 이름 바꾸기 후 Windows 그룹이 기존 컴퓨터 이름을 지정하는 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-125">This can occur after the rename if the Windows group specifies the old computer name.</span></span> <span data-ttu-id="6f6a5-126">이름 바꾸기 작업 후 Windows 그룹이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 연결되도록 하려면 새 컴퓨터 이름을 지정하도록 Windows 그룹을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-126">To ensure that such Windows groups have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connectivity following the renaming operation, update the Windows group to specify the new computer name.</span></span>  
  
 <span data-ttu-id="6f6a5-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서버를 다시 시작하면 새 컴퓨터 이름을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-127">You can connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using the new computer name after you have restarted [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6f6a5-128">@@SERVERNAME에서 로컬 서버 인스턴스의 업데이트된 이름을 반환하도록 하려면 시나리오에 적용되는 다음 절차를 직접 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-128">To ensure that @@SERVERNAME returns the updated name of the local server instance, you should manually run the following procedure that applies to your scenario.</span></span> <span data-ttu-id="6f6a5-129">업데이트하는 컴퓨터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 기본 인스턴스를 호스팅하는지 아니면 명명된 인스턴스를 호스팅하는지 여부에 따라 사용할 절차가 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-129">The procedure you use depends on whether you are updating a computer that hosts a default or named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-rename-a-computer-that-hosts-a-stand-alone-instance-of-ssnoversion"></a><span data-ttu-id="6f6a5-130">다음의 독립 실행형 인스턴스를 호스트하는 컴퓨터의 이름을 바꾸려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f6a5-130">To rename a computer that hosts a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="6f6a5-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 기본 인스턴스를 호스팅하는 컴퓨터의 이름이 바뀐 경우 다음 절차를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-131">For a renamed computer that hosts a default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], run the following procedures:</span></span>  
  
    ```  
    sp_dropserver <old_name>;  
    GO  
    sp_addserver <new_name>, local;  
    GO  
    ```  
  
     <span data-ttu-id="6f6a5-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-132">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="6f6a5-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 명명된 인스턴스를 호스팅하는 컴퓨터의 이름이 바뀐 경우 다음 절차를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-133">For a renamed computer that hosts a named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], run the following procedures:</span></span>  
  
    ```  
    sp_dropserver <old_name\instancename>;  
    GO  
    sp_addserver <new_name\instancename>, local;  
    GO  
    ```  
  
     <span data-ttu-id="6f6a5-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-134">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="after-the-renaming-operation"></a><span data-ttu-id="6f6a5-135">이름 바꾸기 작업을 실행한 후</span><span class="sxs-lookup"><span data-stu-id="6f6a5-135">After the Renaming Operation</span></span>  
 <span data-ttu-id="6f6a5-136">컴퓨터의 이름이 변경되면 이전 컴퓨터 이름을 사용하던 모든 연결은 새 이름을 사용하여 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-136">After a computer has been renamed, any connections that used the old computer name must connect by using the new name.</span></span>  
  
#### <a name="to-verify-that-the-renaming-operation-has-completed-successfully"></a><span data-ttu-id="6f6a5-137">이름 바꾸기 작업이 성공적으로 완료되었는지 여부를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="6f6a5-137">To verify that the renaming operation has completed successfully</span></span>  
  
-   <span data-ttu-id="6f6a5-138">@@SERVERNAME 또는 sys.servers에서 정보를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-138">Select information from either @@SERVERNAME or sys.servers.</span></span> <span data-ttu-id="6f6a5-139">@@SERVERNAME 함수에서 새 이름을 반환하고, sys.servers 테이블에 새 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-139">The @@SERVERNAME function will return the new name, and the sys.servers table will show the new name.</span></span> <span data-ttu-id="6f6a5-140">다음 예제에서는 @@SERVERNAME의 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-140">The following example shows the use of @@SERVERNAME.</span></span>  
  
    ```  
    SELECT @@SERVERNAME AS 'Server Name';  
    ```  
  
## <a name="additional-considerations"></a><span data-ttu-id="6f6a5-141">기타 고려 사항</span><span class="sxs-lookup"><span data-stu-id="6f6a5-141">Additional Considerations</span></span>  
 <span data-ttu-id="6f6a5-142">**원격 로그인** - 컴퓨터에서 원격 로그인을 사용하는 경우 **sp_dropserver** 를 실행하면 다음과 유사한 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-142">**Remote Logins** - If the computer has any remote logins, running **sp_dropserver** might generate an error similar to the following:</span></span>  
  
 `Server: Msg 15190, Level 16, State 1, Procedure sp_dropserver, Line 44 There are still remote logins for the server 'SERVER1'.`  
  
 <span data-ttu-id="6f6a5-143">오류를 해결하려면 이 서버에 대한 원격 로그인을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-143">To resolve the error, you must drop remote logins for this server.</span></span>  
  
#### <a name="to-drop-remote-logins"></a><span data-ttu-id="6f6a5-144">원격 로그인을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="6f6a5-144">To drop remote logins</span></span>  
  
-   <span data-ttu-id="6f6a5-145">기본 인스턴스의 경우 다음 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-145">For a default instance, run the following procedure:</span></span>  
  
    ```  
    sp_dropremotelogin old_name;  
    GO  
    ```  
  
-   <span data-ttu-id="6f6a5-146">명명된 인스턴스의 경우 다음 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-146">For a named instance, run the following procedure:</span></span>  
  
    ```  
    sp_dropremotelogin old_name\instancename;  
    GO  
    ```  
  
 <span data-ttu-id="6f6a5-147">**연결된 서버 구성** - 연결된 서버 구성은 컴퓨터 이름 바꾸기 작업의 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-147">**Linked Server Configurations** - Linked server configurations will be affected by the computer renaming operation.</span></span> <span data-ttu-id="6f6a5-148">`sp_addlinkedserver` 또는 `sp_setnetname`을 사용하여 컴퓨터 이름 참조를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-148">Use `sp_addlinkedserver` or `sp_setnetname` to update computer name references.</span></span> <span data-ttu-id="6f6a5-149">자세한 내용은 [sp_addlinkedserver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) 또는 [sp_setnetname&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setnetname-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-149">For more information, see the [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) or [sp_setnetname &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setnetname-transact-sql).</span></span>  
  
 <span data-ttu-id="6f6a5-150">**클라이언트 별칭** - 명명된 파이프를 사용하는 클라이언트 별칭은 컴퓨터 이름 바꾸기 작업의 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-150">**Client Alias Names** - Client aliases that use named pipes will be affected by the computer renaming operation.</span></span> <span data-ttu-id="6f6a5-151">예를 들어 명명된 파이프 프로토콜을 사용하여 SRVR1을 가리키는 "PROD_SRVR"이라는 별칭을 만든 경우 파이프 이름은 `\\SRVR1\pipe\sql\query`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-151">For example, if an alias "PROD_SRVR" was created to point to SRVR1 and uses the named pipes protocol, the pipe name will look like `\\SRVR1\pipe\sql\query`.</span></span> <span data-ttu-id="6f6a5-152">컴퓨터의 이름을 바꾸면 명명된 파이프의 경로가 더 이상 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-152">After the computer is renamed, the path of the named pipe will no longer be valid and.</span></span> <span data-ttu-id="6f6a5-153">명명된 파이프에 대한 자세한 내용은 [명명된 파이프를 사용하여 유효한 연결 문자열 만들기](https://go.microsoft.com/fwlink/?LinkId=111063)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f6a5-153">For more information about named pipes, see the [Creating a Valid Connection String Using Named Pipes](https://go.microsoft.com/fwlink/?LinkId=111063).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6a5-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f6a5-154">See Also</span></span>  
 [<span data-ttu-id="6f6a5-155">SQL Server 2014 설치</span><span class="sxs-lookup"><span data-stu-id="6f6a5-155">Install SQL Server 2014</span></span>](../../database-engine/install-windows/install-sql-server.md)  
  
  
