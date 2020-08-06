---
title: 정책 기반 관리 정책 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, delete policies
ms.assetid: 488f0305-190c-4223-aa5c-e9bd43b520eb
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c43bc3cdf4a7a5b5d9268bbd7e68506616d1f0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728211"
---
# <a name="delete-a-policy-based-management-policy"></a><span data-ttu-id="99183-102">정책 기반 관리 정책 삭제</span><span class="sxs-lookup"><span data-stu-id="99183-102">Delete a Policy-Based Management Policy</span></span>
  <span data-ttu-id="99183-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 정책 기반 관리 정책을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="99183-103">This topic describes how to delete a Policy-Based Management policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="99183-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="99183-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="99183-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="99183-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="99183-106">보안</span><span class="sxs-lookup"><span data-stu-id="99183-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="99183-107">**다음을 사용하여 정책을 삭제하려면:**</span><span class="sxs-lookup"><span data-stu-id="99183-107">**To delete a policy, using:**</span></span>  
  
     [<span data-ttu-id="99183-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="99183-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="99183-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="99183-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="99183-110">보안</span><span class="sxs-lookup"><span data-stu-id="99183-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="99183-111">권한</span><span class="sxs-lookup"><span data-stu-id="99183-111">Permissions</span></span>  
 <span data-ttu-id="99183-112">msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="99183-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="99183-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="99183-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-policy"></a><span data-ttu-id="99183-114">정책을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="99183-114">To delete a policy</span></span>  
  
1.  <span data-ttu-id="99183-115">개체 탐색기에서 더하기 기호를 클릭하여 삭제할 정책 기반 관리 정책이 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="99183-115">In Object Explorer, click the plus sign to expand the server that contains the Policy-Based Management policy that you want to delete.</span></span>  
  
2.  <span data-ttu-id="99183-116">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="99183-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="99183-117">더하기 기호를 클릭하여 **정책 관리**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="99183-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="99183-118">더하기 기호를 클릭하여 **정책** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="99183-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="99183-119">삭제할 정책을 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99183-119">Right-click the policy that you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="99183-120">**개체 삭제** 대화 상자에서 올바른 조건을 선택했는지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99183-120">In the **Delete Object** dialog box, ensure that the correct condition is selected and then click **OK**.</span></span>  
  
  
