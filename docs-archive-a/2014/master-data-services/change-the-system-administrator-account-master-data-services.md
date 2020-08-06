---
title: 시스템 관리자 계정 변경 (MDS(Master Data Services)) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], changing
ms.assetid: cf30312e-4338-49a7-90f0-6e4f7b431ff8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1d13cdc19c70c9e16c92dfd290393739d7e4f5e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734223"
---
# <a name="change-the-system-administrator-account-master-data-services"></a><span data-ttu-id="de9e2-102">시스템 관리자 계정 변경(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="de9e2-102">Change the System Administrator Account (Master Data Services)</span></span>
  <span data-ttu-id="de9e2-103">시스템 관리자로 지정 된 사용자 계정을 변경할 수 있습니다 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="de9e2-103">You can change the user account that is designated as the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="de9e2-104">이 절차를 완료하면 이전 시스템 관리자의 사용자 계정이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="de9e2-104">When you complete this procedure, the former system administrator user account is deleted.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="de9e2-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="de9e2-105">Prerequisites</span></span>  
 <span data-ttu-id="de9e2-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="de9e2-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="de9e2-107">새 관리자의 사용자 이름을 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 사용자 목록에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de9e2-107">You must add the new administrator's user name to the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Users list.</span></span> <span data-ttu-id="de9e2-108">자세한 내용은 [&#41;MDS(Master Data Services) 사용자 &#40;추가 ](add-a-user-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="de9e2-108">For more information, see [Add a User &#40;Master Data Services&#41;](add-a-user-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="de9e2-109">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에서 mdm.tblUser를 보고 mdm.udpSecurityMemberProcessRebuildModel 저장 프로시저를 실행할 수 있는 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="de9e2-109">You must have permission to view mdm.tblUser and to execute the mdm.udpSecurityMemberProcessRebuildModel stored procedure in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="de9e2-110">자세한 내용은 [데이터베이스 개체 보안&#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="de9e2-110">For more information, see [Database Object Security &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md).</span></span>  
  
### <a name="to-change-the-administrator-account"></a><span data-ttu-id="de9e2-111">관리자 계정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="de9e2-111">To change the administrator account</span></span>  
  
1.  <span data-ttu-id="de9e2-112">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 을 열고 [!INCLUDE[ssDE](../includes/ssde-md.md)] 데이터베이스의 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="de9e2-112">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="de9e2-113">Mdm. tblUser에서 새 관리자로 지정할 사용자를 찾아 해당 값을 열에 복사 `SID` 합니다.</span><span class="sxs-lookup"><span data-stu-id="de9e2-113">In mdm.tblUser, find the user that will be the new administrator and copy the value in the `SID` column.</span></span>  
  
3.  <span data-ttu-id="de9e2-114">새 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="de9e2-114">Create a new query.</span></span>  
  
4.  <span data-ttu-id="de9e2-115">다음 텍스트를 입력 하 여 *DOMAIN \ user_name* 를 2 단계에서 복사한 값으로 새 관리자의 사용자 이름 및 *SID* 로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="de9e2-115">Type the following text, replacing *DOMAIN\user_name* with the new administrator's user name and *SID* with the value you copied in step 2.</span></span>  
  
    ```  
    EXEC [mdm].[udpSecuritySetAdministrator] @UserName='DOMAIN\user_name', @SID = 'SID', @PromoteNonAdmin = 1  
    ```  
  
5.  <span data-ttu-id="de9e2-116">쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="de9e2-116">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de9e2-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="de9e2-117">See Also</span></span>  
 [<span data-ttu-id="de9e2-118">관리자&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="de9e2-118">Administrators &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/administrators-master-data-services.md)  
  
  
