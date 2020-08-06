---
title: 마스터 서버에 대상 서버 등록 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enlisting target servers [SQL Server]
- SQL Server Agent jobs, target servers
- master servers [SQL Server], enlisting target servers
- SQL Server Agent jobs, master servers
- target servers [SQL Server], enlisting
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 256f1a78d298d89a36412ee5689695f3ab3fde8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639227"
---
# <a name="enlist-a-target-server-to-a-master-server"></a><span data-ttu-id="37e1e-102">마스터 서버에 대상 서버 등록</span><span class="sxs-lookup"><span data-stu-id="37e1e-102">Enlist a Target Server to a Master Server</span></span>
  <span data-ttu-id="37e1e-103">이 항목에서는 대상 서버를 다중 서버 관리 구성에 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="37e1e-103">This topic describes how to add target servers to a multiserver administration configuration.</span></span> <span data-ttu-id="37e1e-104">이 절차는 마스터 서버에서 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="37e1e-104">Run this procedure from the master server.</span></span> <span data-ttu-id="37e1e-105">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]또는 SMO(SQL Server 관리 개체)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="37e1e-105">in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="37e1e-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스에 사용되는 Windows 계정이 다중 서버 환경에 미치는 영향에 대한 자세한 내용은 [다중 서버 환경 만들기](create-a-multiserver-environment.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="37e1e-106">For information about how the Windows account used for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service affects a multiserver environment, see [Create a Multiserver Environment](create-a-multiserver-environment.md).</span></span>  
  
 <span data-ttu-id="37e1e-107">전체 SSL(Secure Sockets Layer) 암호화 및 인증서 확인은 기본적으로 마스터 서버와 대상 서버 간 연결에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37e1e-107">Full Secure Sockets Layer (SSL) encryption and certificate validation is enabled for connections between master servers and target servers by default.</span></span> <span data-ttu-id="37e1e-108">자세한 내용은 [대상 서버의 암호화 옵션 설정](set-encryption-options-on-target-servers.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="37e1e-108">For more information, see [Set Encryption Options on Target Servers](set-encryption-options-on-target-servers.md).</span></span>  
  
 <span data-ttu-id="37e1e-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="37e1e-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="37e1e-110">**대상 서버를 등록하려면:**</span><span class="sxs-lookup"><span data-stu-id="37e1e-110">**To enlist a target server, using:**</span></span>  
  
     [<span data-ttu-id="37e1e-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="37e1e-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="37e1e-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="37e1e-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="37e1e-113">SMO</span><span class="sxs-lookup"><span data-stu-id="37e1e-113">SMO</span></span>](#PowerShellProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="37e1e-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="37e1e-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enlist-a-target-server"></a><span data-ttu-id="37e1e-115">대상 서버를 등록하려면</span><span class="sxs-lookup"><span data-stu-id="37e1e-115">To enlist a target server</span></span>  
  
1.  <span data-ttu-id="37e1e-116">**개체 탐색기**에서 마스터 서버로 구성된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="37e1e-116">In **Object Explorer**, expand a server that is configured as a master server.</span></span>  
  
2.  <span data-ttu-id="37e1e-117">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭하고 **다중 서버 관리**를 가리킨 다음 **대상 서버 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="37e1e-117">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Add Target Servers**.</span></span>  
  
3.  <span data-ttu-id="37e1e-118">전체 프로세스를 안내하는 대상 서버 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="37e1e-118">Complete the Target Server Wizard, which guides you through the process.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="37e1e-119">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="37e1e-119">Using Transact-SQL</span></span>  
  
#### <a name="to-enlist-a-target-server"></a><span data-ttu-id="37e1e-120">대상 서버를 등록하려면</span><span class="sxs-lookup"><span data-stu-id="37e1e-120">To enlist a target server</span></span>  
  
1.  <span data-ttu-id="37e1e-121">`sp_msx_enlist` 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="37e1e-121">Use the `sp_msx_enlist` stored procedure.</span></span>  <span data-ttu-id="37e1e-122">자세한 내용은 [sp_msx_enlist &#40;transact-sql](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql) 을 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="37e1e-122">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)</span></span>  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a><span data-ttu-id="37e1e-123">SQL Server 관리 개체 사용 (SMO)</span><span class="sxs-lookup"><span data-stu-id="37e1e-123">Using SQL Server Management Objects (SMO)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e1e-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37e1e-124">See Also</span></span>  
 [<span data-ttu-id="37e1e-125">기업 내 관리 자동화</span><span class="sxs-lookup"><span data-stu-id="37e1e-125">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
