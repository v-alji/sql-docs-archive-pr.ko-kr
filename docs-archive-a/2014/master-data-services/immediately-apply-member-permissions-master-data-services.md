---
title: 멤버 권한 즉시 적용(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], applying permissions immediately
- permissions [Master Data Services], applying member permissions immediately
ms.assetid: 5b16de66-5c39-49f5-992f-402a9eb319aa
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e960ad06213b7c5057a6249b72ce225a6abe35e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652171"
---
# <a name="immediately-apply-member-permissions-master-data-services"></a><span data-ttu-id="ff4ef-102">멤버 권한 즉시 적용(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ff4ef-102">Immediately Apply Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="ff4ef-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 멤버 보안이 일정한 간격으로 적용되기를 기다리는 대신 멤버 권한을 즉시 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff4ef-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], instead of waiting for member security to be applied at regular intervals, you can apply member permissions immediately.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ff4ef-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ff4ef-104">Prerequisites</span></span>  
 <span data-ttu-id="ff4ef-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="ff4ef-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="ff4ef-106">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에서 mdm.udpSecurityMemberProcessRebuildModel 저장 프로시저를 실행할 수 있는 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff4ef-106">You must have permission to execute the mdm.udpSecurityMemberProcessRebuildModel stored procedure in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="ff4ef-107">자세한 내용은 [데이터베이스 개체 보안&#40;Master Data Services&#41;](database-object-security-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff4ef-107">For more information, see [Database Object Security &#40;Master Data Services&#41;](database-object-security-master-data-services.md).</span></span>  
  
### <a name="to-immediately-apply-hierarchy-member-permissions"></a><span data-ttu-id="ff4ef-108">계층 멤버 권한을 즉시 적용하려면</span><span class="sxs-lookup"><span data-stu-id="ff4ef-108">To immediately apply hierarchy member permissions</span></span>  
  
1.  <span data-ttu-id="ff4ef-109">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 을 열고 [!INCLUDE[ssDE](../includes/ssde-md.md)] 데이터베이스의 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ff4ef-109">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="ff4ef-110">새 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ff4ef-110">Create a new query.</span></span>  
  
3.  <span data-ttu-id="ff4ef-111">다음 텍스트를 입력하여 *database* 를 데이터베이스 이름으로 바꾸고 *Model_Name* 을 모델 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ff4ef-111">Type the following text, replacing *database* with the name of your database and *Model_Name* with the name of the model.</span></span>  
  
    ```  
    USE [database];  
    GO  
  
    DECLARE @Model_ID INT;  
    SELECT @Model_ID = ID FROM mdm.tblModel WHERE [Name] = N'Model_Name';  
    EXEC [mdm].[udpSecurityMemberProcessRebuildModel] @Model_ID=@Model_ID, @ProcessNow=1;  
    GO  
    ```  
  
4.  <span data-ttu-id="ff4ef-112">쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ff4ef-112">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff4ef-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ff4ef-113">See Also</span></span>  
 <span data-ttu-id="ff4ef-114">[계층 멤버 권한 할당 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ff4ef-114">[Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="ff4ef-115">계층 멤버 권한&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ff4ef-115">Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
