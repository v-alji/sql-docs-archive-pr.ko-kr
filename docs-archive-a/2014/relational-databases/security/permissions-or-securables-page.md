---
title: 사용 권한 또는 보안 개체 페이지 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.common.permissions.f1
- sql12.swb.SecurableAndEffectPermissions.f1
- sql12.swb.availabilitygroupproperties.permission.f1
- sql12.swb.common.columnperm.f1
- sql12.swb.SecurableAndEffectivePermission.f1
ms.assetid: b3bf077a-bec2-4161-ac0c-460586199906
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 80417c720258833850f07eb67f83f5c47f487ad2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730351"
---
# <a name="permissions-or-securables-page"></a><span data-ttu-id="cefad-102">사용 권한 또는 보안 개체 페이지</span><span class="sxs-lookup"><span data-stu-id="cefad-102">Permissions or Securables Page</span></span>
  <span data-ttu-id="cefad-103">**사용 권한** 페이지 또는 **보안 개체** 페이지를 사용하여 보안 개체에 대한 사용 권한을 보거나 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-103">Use the **Permissions** page or the **Securables** page to view or set the permissions for securables.</span></span> <span data-ttu-id="cefad-104">이 페이지는 여러 위치에서 열 수 있으며</span><span class="sxs-lookup"><span data-stu-id="cefad-104">This page can be opened from many locations.</span></span> <span data-ttu-id="cefad-105">페이지의 내용은 페이지를 연 방법과 페이지에 포함된 항목에 따라 조금씩 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-105">The contents of the page can change slightly, depending on how the page is opened and what it contains.</span></span> <span data-ttu-id="cefad-106">페이지가 열릴 때 해당 페이지의 위쪽 표는 채워져 있거나 비어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-106">The top grid of the page might be populated when the page opens, or it might be empty.</span></span> <span data-ttu-id="cefad-107">상단 표에 항목을 추가하려면 **검색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-107">To add items to the upper grid, click **Search**.</span></span> <span data-ttu-id="cefad-108">상단 표에서 항목을 선택한 다음 **명시적** 탭에서 적절한 사용 권한을 설정합니다. 집계된 사용 권한을 보려면 **유효** 탭을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-108">In the upper grid, select an item, and then set the appropriate permissions on the **Explicit** tab. To view aggregated permissions, use the **Effective** tab.</span></span>  
  
 <span data-ttu-id="cefad-109">가능한 보안 개체와 보안 주체의 조합에 대한 자세한 내용은 [GRANT&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) 항목에서 보안 개체별 구문 링크를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cefad-109">To understand the possible combinations of securables and principals, see the securable-specific syntax links in the topic [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span> <span data-ttu-id="cefad-110">자세한 내용은 [Securables](securables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cefad-110">For more information, see [Securables](securables.md).</span></span>  
  
## <a name="page-header"></a><span data-ttu-id="cefad-111">페이지 머리글</span><span class="sxs-lookup"><span data-stu-id="cefad-111">Page Header</span></span>  
 <span data-ttu-id="cefad-112">**사용 권한** 또는 **보안 개체** 페이지의 머리글은 보안 개체나 보안 주체에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-112">The header of the **Permissions** or **Securables** page varies depending on the securable or principal.</span></span> <span data-ttu-id="cefad-113">이 페이지의 머리글에서는 항목 이름 등 항목과 관련된 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-113">It displays information relevant to the item, such as its name.</span></span>  
  
## <a name="upper-grid"></a><span data-ttu-id="cefad-114">상단 표</span><span class="sxs-lookup"><span data-stu-id="cefad-114">Upper Grid</span></span>  
 <span data-ttu-id="cefad-115">상단 표에는 사용 권한을 설정할 수 있는 항목이 하나 이상 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-115">The upper grid contains one or more items for which permissions can be set.</span></span> <span data-ttu-id="cefad-116">이 대화 상자에는 상단 표에 추가할 개체나 보안 주체를 선택할 수 있는 **검색** 단추가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-116">This dialog box provides the **Search** button for selecting objects or principals to add to the upper grid.</span></span> <span data-ttu-id="cefad-117">표의 이름은 **보안 개체** 나 하나 이상의 보안 개체/보안 주체 유형을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-117">The name of the grid might display **Securables** or one or more types of securables or principals.</span></span> <span data-ttu-id="cefad-118">상단 표에 표시되는 열은 보안 주체 또는 보안 개체에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-118">The columns that are displayed in the upper grid vary depending on the principal or securable.</span></span>  
  
 <span data-ttu-id="cefad-119">**이름**</span><span class="sxs-lookup"><span data-stu-id="cefad-119">**Name**</span></span>  
 <span data-ttu-id="cefad-120">표에 추가된 각 보안 주체 또는 보안 개체의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-120">The name of each principal or securable that is added to the grid.</span></span>  
  
 <span data-ttu-id="cefad-121">**형식**</span><span class="sxs-lookup"><span data-stu-id="cefad-121">**Type**</span></span>  
 <span data-ttu-id="cefad-122">각 항목의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-122">Describes the type of each item.</span></span>  
  
## <a name="explicit-tab"></a><span data-ttu-id="cefad-123">명시적 탭</span><span class="sxs-lookup"><span data-stu-id="cefad-123">Explicit Tab</span></span>  
 <span data-ttu-id="cefad-124">**명시적** 탭에서는 상단 표에서 선택된 보안 개체의 가능한 사용 권한을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-124">The **Explicit** tab lists the possible permissions for the securable that are selected in the upper grid.</span></span> <span data-ttu-id="cefad-125">사용 권한을 구성하려면 **권한 부여** (또는 **허용**), **허용 권한 소유**및 **거부** 확인란을 선택하거나 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-125">To configure the permissions, select or clear the **Grant** (or **Allow**), **With Grant**, and **Deny** check boxes.</span></span> <span data-ttu-id="cefad-126">모든 명시적 사용 권한에 대해 모든 옵션을 사용할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-126">All options are not available for all explicit permissions.</span></span>  
  
 <span data-ttu-id="cefad-127">**권한**</span><span class="sxs-lookup"><span data-stu-id="cefad-127">**Permissions**</span></span>  
 <span data-ttu-id="cefad-128">사용 권한의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-128">The name of the permission.</span></span>  
  
 <span data-ttu-id="cefad-129">**Grantor**</span><span class="sxs-lookup"><span data-stu-id="cefad-129">**Grantor**</span></span>  
 <span data-ttu-id="cefad-130">사용 권한을 부여한 보안 주체입니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-130">The principal that granted the permission.</span></span>  
  
 <span data-ttu-id="cefad-131">**허용**</span><span class="sxs-lookup"><span data-stu-id="cefad-131">**Grant**</span></span>  
 <span data-ttu-id="cefad-132">로그인에 이 사용 권한을 허용하려면 선택하고</span><span class="sxs-lookup"><span data-stu-id="cefad-132">Select to grant this permission to the login.</span></span> <span data-ttu-id="cefad-133">사용 권한을 해제하려면 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-133">Clear to revoke this permission.</span></span>  
  
 <span data-ttu-id="cefad-134">**허용 권한 소유**</span><span class="sxs-lookup"><span data-stu-id="cefad-134">**With Grant**</span></span>  
 <span data-ttu-id="cefad-135">나열된 사용 권한에 대한 WITH GRANT 옵션 상태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-135">Reflects the state of the WITH GRANT option for the listed permission.</span></span> <span data-ttu-id="cefad-136">이 부분은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-136">This box is read-only.</span></span> <span data-ttu-id="cefad-137">이 사용 권한을 적용하려면 [GRANT](/sql/t-sql/statements/grant-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-137">To apply this permission, use the [GRANT](/sql/t-sql/statements/grant-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="cefad-138">**거부**</span><span class="sxs-lookup"><span data-stu-id="cefad-138">**Deny**</span></span>  
 <span data-ttu-id="cefad-139">로그인에 이 사용 권한을 거부하려면 선택하고</span><span class="sxs-lookup"><span data-stu-id="cefad-139">Select to deny this permission to the login.</span></span> <span data-ttu-id="cefad-140">사용 권한을 해제하려면 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-140">Clear to revoke this permission.</span></span>  
  
 <span data-ttu-id="cefad-141">**열 사용 권한**</span><span class="sxs-lookup"><span data-stu-id="cefad-141">**Column Permissions**</span></span>  
 <span data-ttu-id="cefad-142">열(예: 테이블, 뷰, 테이블 반환 함수)을 포함하는 개체의 경우 **열 사용 권한** 단추를 누르면 **열 사용 권한** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-142">For objects that contain columns (such as tables, views, or table-valued functions), the **Column Permissions** button opens the **Column Permissions** dialog box.</span></span> <span data-ttu-id="cefad-143">이 대화 상자에서 각 테이블 또는 뷰 열에 **권한 부여**, **허용**또는 **거부** 권한을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-143">In this dialog box, you can set **Grant**, **Allow**, or **Deny** permissions on individual columns of a table or view.</span></span> <span data-ttu-id="cefad-144">일부 개체 유형 또는 사용 권한의 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-144">This option is not available for all object types or permissions.</span></span>  
  
## <a name="effective-tab"></a><span data-ttu-id="cefad-145">유효 탭</span><span class="sxs-lookup"><span data-stu-id="cefad-145">Effective Tab</span></span>  
 <span data-ttu-id="cefad-146">보안 개체와 관련된 보안 주체의 사용 권한은 여러 가지 보안 주체에 대해 설정된 사용 권한에서 가져온 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-146">The permissions that a principal has related to a securable may come from permissions that are set for several different principals.</span></span> <span data-ttu-id="cefad-147">예를 들어 로그인에 사용 권한을 개별적으로 부여할 수 있으며 그룹 멤버로서 부여할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-147">For example, a login might be granted permissions individually and also as a member of a group.</span></span> <span data-ttu-id="cefad-148">**유효** 탭에서는 명시적 사용 권한과 그룹 또는 역할 멤버 자격으로부터 가져온 사용 권한을 조합한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-148">The **Effective** tab shows the result of combining explicit permissions and the permissions that are received from group or role memberships.</span></span> <span data-ttu-id="cefad-149">허용 권한은 집계되며</span><span class="sxs-lookup"><span data-stu-id="cefad-149">Grant permissions are aggregated.</span></span> <span data-ttu-id="cefad-150">거부 권한은 모든 허용 권한보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-150">A deny permission overrides all grant permissions.</span></span>  
  
 <span data-ttu-id="cefad-151">**권한**</span><span class="sxs-lookup"><span data-stu-id="cefad-151">**Permissions**</span></span>  
 <span data-ttu-id="cefad-152">사용 권한의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-152">The name of the permission.</span></span>  
  
 <span data-ttu-id="cefad-153">**열**</span><span class="sxs-lookup"><span data-stu-id="cefad-153">**Column**</span></span>  
 <span data-ttu-id="cefad-154">사용 권한의 영향을 받은 열의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="cefad-154">The names of columns that are affected by the permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cefad-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cefad-155">See Also</span></span>  
 <span data-ttu-id="cefad-156">[데이터베이스 수준 역할](authentication-access/database-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="cefad-156">[Database-Level Roles](authentication-access/database-level-roles.md) </span></span>  
 [<span data-ttu-id="cefad-157">SQL Server 데이터베이스 엔진 및 Azure SQL Database 보안 센터</span><span class="sxs-lookup"><span data-stu-id="cefad-157">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
