---
title: 새로운 정책 기반 관리 조건 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, creating policy conditions
ms.assetid: 8a612f7e-6c70-49db-a4de-48431e097cc5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e4fe206c9a82b69101508f6f0a760ca9c1bc423d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651671"
---
# <a name="create-a-new-policy-based-management-condition"></a><span data-ttu-id="51d90-102">새로운 정책 기반 관리 조건 만들기</span><span class="sxs-lookup"><span data-stu-id="51d90-102">Create a New Policy-Based Management Condition</span></span>
  <span data-ttu-id="51d90-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 정책 기반 관리 조건을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="51d90-103">This topic describes how to create a Policy-based Management condition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="51d90-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="51d90-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="51d90-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="51d90-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="51d90-106">보안</span><span class="sxs-lookup"><span data-stu-id="51d90-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="51d90-107">**다음을 사용하여 조건을 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="51d90-107">**To create a condition, using:**</span></span>  
  
     [<span data-ttu-id="51d90-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="51d90-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="51d90-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="51d90-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="51d90-110">보안</span><span class="sxs-lookup"><span data-stu-id="51d90-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="51d90-111">권한</span><span class="sxs-lookup"><span data-stu-id="51d90-111">Permissions</span></span>  
 <span data-ttu-id="51d90-112">msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="51d90-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="51d90-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="51d90-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-condition"></a><span data-ttu-id="51d90-114">조건을 만들려면</span><span class="sxs-lookup"><span data-stu-id="51d90-114">To create a condition</span></span>  
  
1.  <span data-ttu-id="51d90-115">**개체 탐색기**에서 더하기 기호를 클릭하여 정책 기반 관리 조건을 만들려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="51d90-115">In **Object Explorer**, click the plus sign to expand the server where you want to create a Policy-based Management condition.</span></span>  
  
2.  <span data-ttu-id="51d90-116">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="51d90-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="51d90-117">더하기 기호를 클릭하여 **정책 관리**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="51d90-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="51d90-118">더하기 기호를 클릭하여 **패싯** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="51d90-118">Click the plus sign to expand the **Facets** folder.</span></span>  
  
5.  <span data-ttu-id="51d90-119">새 조건을 만들려는 패싯을 마우스 오른쪽 단추로 클릭하고 **새 조건**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="51d90-119">Right-click the facet in which you want to create a new condition and select **New Condition**.</span></span>  
  
6.  <span data-ttu-id="51d90-120">**새 조건 만들기** 대화 상자의 **이름** 상자에 새 조건의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="51d90-120">In the **Create New Condition** dialog box, in the **Name** box, type the name of the new condition.</span></span>  
  
7.  <span data-ttu-id="51d90-121">**패싯** 목록에서 올바른 패싯을 확인하거나 다른 패싯을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="51d90-121">Confirm the correct facet in the **Facet** list, or select a different facet.</span></span>  
  
8.  <span data-ttu-id="51d90-122">**식**의 **필드** 상자에서 패싯 속성과 관련 연산자 및 값을 선택하여 조건 식을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="51d90-122">Under **Expression**, construct condition expressions by selecting a facet property in the **Field** box, together with its associated operator and value.</span></span> <span data-ttu-id="51d90-123">여러 식을 추가할 때 **And** 또는 **Or**를 사용하여 식을 조인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d90-123">When you add multiple expressions, the expressions can be joined by using **And** or **Or**.</span></span> <span data-ttu-id="51d90-124">이 대화 상자에서 사용할 수 있는 옵션에 대한 자세한 내용은 [새 조건 만들기 또는 조건 열기 대화 상자, 일반 페이지](../../integration-services/general-page-of-integration-services-designers-options.md), [새 조건 만들기 또는 조건 열기 대화 상자, 설명 페이지](create-new-condition-or-open-condition-dialog-box-description-page.md) 및 [고급 편집&#40;조건&#41; 대화 상자](advanced-edit-condition-dialog-box.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51d90-124">For more information on the available options in this dialog box, see [Create New Condition or Open Condition Dialog Box, General Page](../../integration-services/general-page-of-integration-services-designers-options.md), [Create New Condition or Open Condition Dialog Box, Description Page](create-new-condition-or-open-condition-dialog-box-description-page.md), and [Advanced Edit &#40;Condition&#41; Dialog Box](advanced-edit-condition-dialog-box.md).</span></span>  
  
9. <span data-ttu-id="51d90-125">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51d90-125">When finished, click **OK**.</span></span>  
  
  
