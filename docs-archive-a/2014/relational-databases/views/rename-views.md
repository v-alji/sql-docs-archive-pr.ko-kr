---
title: 뷰 이름 바꾸기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- renaming views
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5cc76ced033a69788270c3fa9277bcca6972e080
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729320"
---
# <a name="rename-views"></a><span data-ttu-id="d02c3-102">뷰 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="d02c3-102">Rename Views</span></span>
  <span data-ttu-id="d02c3-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 뷰 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-103">You can rename a view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="d02c3-104">뷰의 이름을 바꾸면 해당 뷰와 관련된 코드와 애플리케이션에 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-104">If you rename a view, code and applications that depend on the view may fail.</span></span> <span data-ttu-id="d02c3-105">여기에는 기타 뷰, 쿼리, 저장 프로시저, 사용자 정의 함수, 클라이언트 애플리케이션 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-105">These include other views, queries, stored procedures, user-defined functions, and client applications.</span></span> <span data-ttu-id="d02c3-106">이러한 문제는 연쇄적인 파급 효과를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-106">Note that these failures will cascade.</span></span>  
  
 <span data-ttu-id="d02c3-107">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="d02c3-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d02c3-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="d02c3-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d02c3-109">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="d02c3-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="d02c3-110">보안</span><span class="sxs-lookup"><span data-stu-id="d02c3-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d02c3-111">**뷰 이름을 바꾸려면:**</span><span class="sxs-lookup"><span data-stu-id="d02c3-111">**To rename a view, using:**</span></span>  
  
     [<span data-ttu-id="d02c3-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d02c3-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d02c3-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d02c3-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="d02c3-114">**후속 작업:**  [뷰 이름을 바꾼 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="d02c3-114">**Follow Up:**  [After renaming a view](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d02c3-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d02c3-115">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="d02c3-116">필수 조건</span><span class="sxs-lookup"><span data-stu-id="d02c3-116">Prerequisites</span></span>  
 <span data-ttu-id="d02c3-117">뷰의 모든 종속성 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-117">Obtain a list of all dependencies on the view.</span></span> <span data-ttu-id="d02c3-118">뷰를 참조하는 모든 개체, 스크립트 또는 애플리케이션은 새 뷰 이름을 반영하도록 수정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-118">Any objects, scripts or applications that reference the view must be modified to reflect the new name of the view.</span></span> <span data-ttu-id="d02c3-119">자세한 내용은 [Get Information About a View](get-information-about-a-view.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d02c3-119">For more information, see [Get Information About a View](get-information-about-a-view.md).</span></span> <span data-ttu-id="d02c3-120">뷰 이름을 바꾸는 것보다 뷰를 삭제하고 새로운 이름으로 다시 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-120">We recommend that you drop the view and recreate it with a new name instead of renaming the view.</span></span> <span data-ttu-id="d02c3-121">뷰를 다시 만들면 뷰에 참조된 개체에 대한 종속성 정보가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-121">By recreating the view, you update the dependency information for the objects that are referenced in the view.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d02c3-122">보안</span><span class="sxs-lookup"><span data-stu-id="d02c3-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d02c3-123">권한</span><span class="sxs-lookup"><span data-stu-id="d02c3-123">Permissions</span></span>  
 <span data-ttu-id="d02c3-124">SCHEMA에 대한 ALTER 권한, OBJECT에 대한 CONTROL 권한 및 데이터베이스의 CREATE VIEW 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-124">Requires ALTER permission on SCHEMA or CONTROL permission on OBJECT is required, and CREATE VIEW permission in the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d02c3-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="d02c3-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-view"></a><span data-ttu-id="d02c3-126">뷰 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="d02c3-126">To rename a view</span></span>  
  
1.  <span data-ttu-id="d02c3-127">**개체 탐색기**에서 이름을 바꿀 뷰가 포함된 데이터베이스를 확장한 다음 **뷰** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-127">In **Object Explorer**, expand the database that contains the view you wish to rename and then expand the **View** folder.</span></span>  
  
2.  <span data-ttu-id="d02c3-128">이름을 바꿀 뷰를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-128">Right-click the view you wish to rename and select **Rename**.</span></span>  
  
3.  <span data-ttu-id="d02c3-129">뷰의 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-129">Enter the view's new name.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d02c3-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="d02c3-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="d02c3-131">**뷰 이름을 바꾸려면**</span><span class="sxs-lookup"><span data-stu-id="d02c3-131">**To rename a view**</span></span>  
  
 <span data-ttu-id="d02c3-132">**sp_rename** 을 사용하여 뷰 이름을 변경할 수도 있지만 기존 뷰를 삭제하고 새 이름으로 뷰를 다시 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-132">While you can use **sp_rename** to change the name of the view, we recommend that you delete the existing view and then re-create it with the new name.</span></span>  
  
 <span data-ttu-id="d02c3-133">자세한 내용은 [CREATE VIEW&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) 및 [DROP VIEW&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d02c3-133">For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) and [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql).</span></span>  
  
##  <a name="follow-up-after-renaming-a-view"></a><a name="FollowUp"></a> <span data-ttu-id="d02c3-134">후속 작업: 뷰 이름을 바꾼 후</span><span class="sxs-lookup"><span data-stu-id="d02c3-134">Follow Up: After Renaming a View</span></span>  
 <span data-ttu-id="d02c3-135">뷰의 이전 이름을 참조하는 모든 개체, 스크립트 및 애플리케이션이 이제 새 이름을 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d02c3-135">Ensure that all objects, scripts, and applications that reference the view's old name now use the new name.</span></span>  
  
  
