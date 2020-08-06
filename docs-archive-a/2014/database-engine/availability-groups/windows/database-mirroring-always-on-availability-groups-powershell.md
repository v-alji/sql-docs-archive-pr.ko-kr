---
title: AlwaysOn 가용성 그룹 (SQL Server PowerShell)에 대 한 데이터베이스 미러링 끝점 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], endpoint
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 56058ff8aa72d2471381dd87fb25a3b68356ed36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743432"
---
# <a name="create-a-database-mirroring-endpoint-for-alwayson-availability-groups-sql-server-powershell"></a><span data-ttu-id="34aed-102">AlwaysOn 가용성 그룹에 대한 데이터베이스 미러링 엔드포인트 만들기(SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="34aed-102">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups (SQL Server PowerShell)</span></span>
  <span data-ttu-id="34aed-103">이 항목에서는 PowerShell을 사용하여 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]에서 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에 사용할 데이터베이스 미러링 엔드포인트를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="34aed-103">This topic describes how to create a database mirroring endpoint for use by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using PowerShell.</span></span>  
  
 <span data-ttu-id="34aed-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="34aed-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="34aed-105">**시작하기 전 주의 사항:**  [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="34aed-105">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="34aed-106">**데이터베이스 미러링 엔드포인트를 만드는 데 사용되는 도구:**  [PowerShell](#PowerShellProcedure)</span><span class="sxs-lookup"><span data-stu-id="34aed-106">**To create a database mirroring endpoint, using:**  [PowerShell](#PowerShellProcedure)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="34aed-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="34aed-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="34aed-108">보안</span><span class="sxs-lookup"><span data-stu-id="34aed-108">Security</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="34aed-109">RC4 알고리즘은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34aed-109">The RC4 algorithm is deprecated.</span></span> [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="34aed-110">AES를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="34aed-110">We recommend that you use AES.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="34aed-111">권한</span><span class="sxs-lookup"><span data-stu-id="34aed-111">Permissions</span></span>  
 <span data-ttu-id="34aed-112">CREATE ENDPOINT 권한 또는 sysadmin 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="34aed-112">Requires CREATE ENDPOINT permission, or membership in the sysadmin fixed server role.</span></span> <span data-ttu-id="34aed-113">자세한 내용은 [GRANT 엔드포인트 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34aed-113">For more information, see [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="34aed-114">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="34aed-114">Using PowerShell</span></span>  
 <span data-ttu-id="34aed-115">**데이터베이스 미러링 엔드포인트를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="34aed-115">**To create a database mirroring endpoint**</span></span>  
  
1.  <span data-ttu-id="34aed-116">데이터베이스 미러링 엔드포인트를 만들 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="34aed-116">Change directory (`cd`) to the server instance for which you want to create the database mirroring endpoint.</span></span>  
  
2.  <span data-ttu-id="34aed-117">ph x="1" /&gt; cmdlet을 사용하여 엔드포인트를 만든 다음 `Set-SqlHadrEndpoint`를 사용하여 엔드포인트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="34aed-117">Use the `New-SqlHadrEndpoint` cmdlet to create the endpoint and then use the `Set-SqlHadrEndpoint` to start the endpoint.</span></span>  
  
###  <a name="example-powershell"></a><a name="PShellExample"></a> <span data-ttu-id="34aed-118">예제(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="34aed-118">Example (PowerShell)</span></span>  
 <span data-ttu-id="34aed-119">다음 PowerShell 명령은 SQL Server 인스턴스 (*컴퓨터* \\ *인스턴스*)에 데이터베이스 미러링 끝점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="34aed-119">The following PowerShell commands create a database mirroring endpoint on an instance of SQL Server (*Machine*\\*Instance*).</span></span> <span data-ttu-id="34aed-120">이 엔드포인트는 포트 5022를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="34aed-120">The endpoint uses port 5022.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="34aed-121">이 예는 데이터베이스 미러링 엔드포인트가 현재 없는 서버 인스턴스에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="34aed-121">This example works only on a server instance that currently lack a database mirroring endpoint.</span></span>  
  
```powershell
# Create the endpoint.  
$endpoint = New-SqlHadrEndpoint MyMirroringEndpoint -Port 5022 -Path SQLSERVER:\SQL\Machine\Instance  
  
# Start the endpoint  
Set-SqlHadrEndpoint -InputObject $endpoint -State "Started"
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="34aed-122">관련 작업</span><span class="sxs-lookup"><span data-stu-id="34aed-122">Related Tasks</span></span>  
 <span data-ttu-id="34aed-123">**데이터베이스 미러링 엔드포인트를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="34aed-123">**To Configure a Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="34aed-124">Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="34aed-124">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="34aed-125">데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="34aed-125">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [<span data-ttu-id="34aed-126">데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="34aed-126">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [<span data-ttu-id="34aed-127">데이터베이스 미러링 엔드포인트의 인바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="34aed-127">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="34aed-128">서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;</span><span class="sxs-lookup"><span data-stu-id="34aed-128">Specify a Server Network Address &#40;Database Mirroring&#41;</span></span>](../../database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [<span data-ttu-id="34aed-129">가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="34aed-129">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="34aed-130">**데이터베이스 미러링 엔드포인트에 대한 정보를 보려면**</span><span class="sxs-lookup"><span data-stu-id="34aed-130">**To View Information About the Database Mirroring Endpoint**</span></span>  
  
-   [<span data-ttu-id="34aed-131">sys.database_mirroring_endpoints&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="34aed-131">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="34aed-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34aed-132">See Also</span></span>  
 <span data-ttu-id="34aed-133">[Transact-sql&#41;&#40;가용성 그룹 만들기](create-an-availability-group-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="34aed-133">[Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md) </span></span>  
 [<span data-ttu-id="34aed-134">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="34aed-134">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
