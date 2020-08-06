---
title: 데이터베이스 미러링 모니터 서버 추가 또는 바꾸기(SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], establishing
- database mirroring [SQL Server], witness
ms.assetid: 4b5ecffd-f025-4ab7-b69d-8958c6477127
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5dd14ace23956ceef114f1f032b5d4db5febcec7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648583"
---
# <a name="add-or-replace-a-database-mirroring-witness-sql-server-management-studio"></a><span data-ttu-id="f69cf-102">데이터베이스 미러링 모니터 서버 추가 또는 바꾸기(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f69cf-102">Add or Replace a Database Mirroring Witness (SQL Server Management Studio)</span></span>
  <span data-ttu-id="f69cf-103">데이터베이스 미러링 엔드포인트에서 Windows 인증을 사용하는 경우 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 미러링 모니터 서버를 추가하거나 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-103">If the database mirroring endpoints use Windows Authentication,, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to add or replace a witness.</span></span> <span data-ttu-id="f69cf-104">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 미러링 모니터 서버를 추가하면 운영 모드도 자동 장애 조치(Failover)가 있는 보호 우선 모드로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-104">Adding a witness in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] also changes the operating mode to high-safety mode with automatic failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f69cf-105">미러링 모니터 서버는 파트너 중 별도의 컴퓨터에 있는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-105">We strongly recommend that the witness reside on a separate computer from either of the partners.</span></span> <span data-ttu-id="f69cf-106">미러링 모니터 서버에서 사용하는 서비스 계정은 주 서버 인스턴스 및 미러 서버 인스턴스에서 사용하는 서비스 계정과 같은 도메인에 있거나 트러스트된 도메인에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-106">The service account used by the witness must be in the same domain as the service accounts used by the principal and mirror server instances, or it must be in a trusted domain.</span></span>  
  
### <a name="to-add-or-replace-a-witness"></a><span data-ttu-id="f69cf-107">미러링 모니터 서버를 추가하거나 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="f69cf-107">To Add or Replace a Witness</span></span>  
  
1.  <span data-ttu-id="f69cf-108">주 서버 인스턴스에 연결한 다음 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-108">After connecting to the principal server instance, in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="f69cf-109">**데이터베이스**를 확장한 다음 미러링 모니터 서버를 추가하거나 바꿀 세션의 주 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-109">Expand **Databases**, and select the principal database of the session to which you are adding or replacing a witness.</span></span>  
  
3.  <span data-ttu-id="f69cf-110">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 선택한 다음 **미러**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-110">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="f69cf-111">**데이터베이스 속성** 대화 상자의 **미러링** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-111">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="f69cf-112">**보안 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-112">Click **Configure Security**.</span></span>  
  
5.  <span data-ttu-id="f69cf-113">**데이터베이스 미러링 보안 구성 마법사** 시작 화면이 나타나면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-113">If the **Configure Database Mirroring Security Wizard** welcome screen appears, click **Next**.</span></span>  
  
6.  <span data-ttu-id="f69cf-114">**미러링 모니터 서버 포함** 대화 상자에서 **예**를 클릭한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-114">In the **Include Witness Server** dialog box, click **Yes**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="f69cf-115">**구성할 서버 선택** 대화 상자에서 **미러링 모니터 서버 인스턴스** 확인란이 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-115">In the **Choose Servers to Configure** dialog box, the **Witness server instance** check box is automatically checked.</span></span> <span data-ttu-id="f69cf-116">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-116">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="f69cf-117">**주 서버 인스턴스** 대화 상자에서 기존 포트와 엔드포인트를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-117">On the **Principal Server Instance** dialog box, keep the existing port and endpoint.</span></span> <span data-ttu-id="f69cf-118">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-118">Click **Next**.</span></span>  
  
9. <span data-ttu-id="f69cf-119">**미러링 모니터 서버 인스턴스** 대화 상자에서 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-119">On the **Witness Server Instance** dialog box, click **Connect**.</span></span>  
  
10. <span data-ttu-id="f69cf-120">**서버에 연결** 대화 상자에서 **서버 이름** 필드에 미러링 모니터 서버 인스턴스를 지정하고 Windows 인증(기본값)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-120">In the **Connect to Server** dialog box, specify the witness server instance in the **Server name** field, and use Windows Authentication (the default).</span></span> <span data-ttu-id="f69cf-121">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-121">Click **Connect**.</span></span>  
  
11. <span data-ttu-id="f69cf-122">연결이 설정되면 미러링 모니터 서버 인스턴스의 수신기 포트와 데이터베이스 미러링 엔드포인트가 **미러링 모니터 서버 인스턴스** 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-122">Once a connection is established, the listener port and database mirroring endpoint of the witness server instance are displayed on the **Witness Server Instance** dialog box.</span></span> <span data-ttu-id="f69cf-123">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-123">Click **Next**.</span></span>  
  
12. <span data-ttu-id="f69cf-124">**서비스 계정** 대화 상자에는 주 서버 인스턴스, 미러 서버 인스턴스 및 미러링 모니터 서버 인스턴스의 도메인 서비스 계정에 대한 필드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-124">The **Service Accounts** dialog box contains fields for the domain service accounts of the principal, mirror, and witness server instances.</span></span>  
  
    -   <span data-ttu-id="f69cf-125">모든 서버 인스턴스에서 같은 서비스 계정을 사용하는 경우 필드를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-125">If the server instances all use the same service account, leave the fields blank.</span></span>  
  
    -   <span data-ttu-id="f69cf-126">미러링 모니터 서버 인스턴스에서 파트너 중 하나와 다른 서비스 계정을 사용하는 경우에는 **주 서버**, **미러 서버**및 **미러링 모니터 서버** 필드에 계정 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-126">If the witness server instance uses a different service account from either of the partners, fill in the **Principal**, **Mirror**, and **Witness** fields with the account name:</span></span>  
  
         <span data-ttu-id="f69cf-127">*DOMAINNAME* **\\** *username*</span><span class="sxs-lookup"><span data-stu-id="f69cf-127">*DOMAINNAME* **\\** *username*</span></span>  
  
         <span data-ttu-id="f69cf-128">도메인 이름은 대문자로 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-128">The domain name must be in upper case.</span></span>  
  
     <span data-ttu-id="f69cf-129">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-129">Click **Next**.</span></span>  
  
13. <span data-ttu-id="f69cf-130">필요에 따라 **마법사 완료** 요약 화면에서 미러링 모니터 서버 구성을 확인한 다음 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-130">On the **Complete the Wizard** summary screen, optionally, verify the witness configuration, and then click **Finish**.</span></span>  
  
14. <span data-ttu-id="f69cf-131">마침을 클릭하면 마법사가 **데이터베이스 속성** 대화 상자로 돌아가고 이제 이 대화 상자의 **미러링 모니터 서버** 필드에 미러링 모니터 서버의 서버 네트워크 주소가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-131">On finishing, the wizard returns you to the **Database Properties** dialog box where the server network address of the witness now appears in **Witness** field.</span></span> <span data-ttu-id="f69cf-132">또한 미러링 모니터 서버에 필요한 **자동 장애 조치(Failover)가 있는 보호 우선(동기) 모드**가 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-132">Also, **High-safety mode with automatic failover (synchronous)**, which is required with a witness, is automatically selected.</span></span>  
  
     <span data-ttu-id="f69cf-133">미러링 모니터 서버를 설정하고 세션을 자동 장애 조치(Failover)가 있는 보호 우선 모드로 변경하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f69cf-133">To enable the witness and change the session to high-safety mode with automatic failover, Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f69cf-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f69cf-134">See Also</span></span>  
 <span data-ttu-id="f69cf-135">[데이터베이스 미러링 모니터 서버](database-mirroring-witness.md) </span><span class="sxs-lookup"><span data-stu-id="f69cf-135">[Database Mirroring Witness](database-mirroring-witness.md) </span></span>  
 <span data-ttu-id="f69cf-136">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f69cf-136">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="f69cf-137">[데이터베이스 속성&#40;미러링 페이지&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="f69cf-137">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="f69cf-138">[Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) </span><span class="sxs-lookup"><span data-stu-id="f69cf-138">[Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md) </span></span>  
 [<span data-ttu-id="f69cf-139">데이터베이스 미러링 모니터 서버</span><span class="sxs-lookup"><span data-stu-id="f69cf-139">Database Mirroring Witness</span></span>](database-mirroring-witness.md)  
  
  
