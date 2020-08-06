---
title: 개체의 정책 기반 관리 정책 평가 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: b9e9d646-4894-4dee-a02a-0c71a8dc020e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f0de02092c87a727b723a5940805f34a75052e5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652770"
---
# <a name="evaluate-a-policy-based-management-policy-from-an-object"></a><span data-ttu-id="8902a-102">개체의 정책 기반 관리 정책 평가</span><span class="sxs-lookup"><span data-stu-id="8902a-102">Evaluate a Policy-Based Management Policy from an Object</span></span>
  <span data-ttu-id="8902a-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 서버 인스턴스, 데이터베이스 또는 데이터베이스 개체의 정책을 평가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8902a-103">This topic describes how to evaluate a policy from a server instance, database, or database object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="8902a-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="8902a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8902a-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="8902a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8902a-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8902a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8902a-107">보안</span><span class="sxs-lookup"><span data-stu-id="8902a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8902a-108">**다음을 사용하여 개체의 정책을 평가하려면:**</span><span class="sxs-lookup"><span data-stu-id="8902a-108">**To evaluate a policy from an object, using:**</span></span>  
  
     [<span data-ttu-id="8902a-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8902a-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8902a-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8902a-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8902a-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8902a-111">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="8902a-112">실행 모드는 정책의 일부로 정의되어 있으며 **정책 평가** 대화 상자에서 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8902a-112">The execution mode is defined as part of the policy and cannot be changed in the **Evaluate Policies** dialog box.</span></span>  
  
-   <span data-ttu-id="8902a-113">**정책 평가** 대화 상자에는 데이터베이스 개체에 적합한 정책만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8902a-113">The **Evaluate Policies** dialog box only shows policies appropriate for the database object.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8902a-114">보안</span><span class="sxs-lookup"><span data-stu-id="8902a-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8902a-115">권한</span><span class="sxs-lookup"><span data-stu-id="8902a-115">Permissions</span></span>  
 <span data-ttu-id="8902a-116">msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8902a-116">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8902a-117">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="8902a-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-evaluate-a-policy-from-an-object"></a><span data-ttu-id="8902a-118">개체의 정책을 평가하려면</span><span class="sxs-lookup"><span data-stu-id="8902a-118">To evaluate a policy from an object</span></span>  
  
1.  <span data-ttu-id="8902a-119">개체 탐색기에서 서버 인스턴스, 데이터베이스 또는 데이터베이스 개체를 마우스 오른쪽 단추로 클릭하고 **정책**을 가리킨 다음 **평가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8902a-119">In Object Explorer, right-click a server instance, a database, or a database object, point to **Policies**, and select **Evaluate**.</span></span>  
  
2.  <span data-ttu-id="8902a-120">**정책 평가** 대화 상자에서 하나 이상의 정책을 선택하고 **평가** 를 클릭하여 평가 모드에서 정책을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8902a-120">In the **Evaluate Policies** dialog box, select one or more policies and click **Evaluate** to run the policy in evaluation mode.</span></span> <span data-ttu-id="8902a-121">이렇게 하면 대상 집합에 대한 준수 보고서가 생성되지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 다시 구성되거나 앞으로 정책이 준수되도록 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8902a-121">This generates a compliance report for the target set but does not reconfigure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or enforce future compliance.</span></span> <span data-ttu-id="8902a-122">선택한 정책을 따르지 않고 정책 기반 관리로 다시 구성할 수 있는 속성이 있는 대상의 경우 **적용**을 클릭하여 정책 준수를 강제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8902a-122">For targets that do not comply with the selected policies and have properties that can be reconfigured by Policy-Based Management, you can enforce policy compliance by clicking **Apply**.</span></span> <span data-ttu-id="8902a-123">**정책 평가** 대화 상자에서 사용할 수 있는 옵션에 대한 자세한 내용은 [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md), [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md)및 [Results Detailed View Dialog Box](results-detailed-view-dialog-box.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8902a-123">For more information on the available options in the **Evaluate Policies** dialog box, see [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md), [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md), and [Results Detailed View Dialog Box](results-detailed-view-dialog-box.md).</span></span>  
  
3.  <span data-ttu-id="8902a-124">완료되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8902a-124">When finished, click **Close**.</span></span>  
  
  
