---
title: 정책 기반 관리 정책의 정책 평가 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: 0b3214bd-d0ab-45ab-9281-3d95507abe54
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 207c86f1465c49238fc9b50ee75489b43d956caf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652772"
---
# <a name="evaluate-a-policy-based-management-policy-from-that-policy"></a><span data-ttu-id="624c7-102">정책 기반 관리 정책의 정책 평가</span><span class="sxs-lookup"><span data-stu-id="624c7-102">Evaluate a Policy-Based Management Policy from That Policy</span></span>
  <span data-ttu-id="624c7-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 정책을 통해 해당 정책을 평가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="624c7-103">This topic describes how to evaluate a policy using that policy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="624c7-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="624c7-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="624c7-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="624c7-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="624c7-106">보안</span><span class="sxs-lookup"><span data-stu-id="624c7-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="624c7-107">**다음을 사용하여 정책을 평가하려면:**</span><span class="sxs-lookup"><span data-stu-id="624c7-107">**To evaluate a policy, using:**</span></span>  
  
     [<span data-ttu-id="624c7-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="624c7-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="624c7-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="624c7-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="624c7-110">보안</span><span class="sxs-lookup"><span data-stu-id="624c7-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="624c7-111">권한</span><span class="sxs-lookup"><span data-stu-id="624c7-111">Permissions</span></span>  
 <span data-ttu-id="624c7-112">msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="624c7-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="624c7-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="624c7-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-evaluate-a-policy"></a><span data-ttu-id="624c7-114">정책을 평가하려면</span><span class="sxs-lookup"><span data-stu-id="624c7-114">To evaluate a policy</span></span>  
  
1.  <span data-ttu-id="624c7-115">**개체 탐색기**에서 더하기 기호를 클릭하여 평가할 정책이 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="624c7-115">In **Object Explorer**, click the plus sign to expand the server that contains the policy that you want to evaluate.</span></span>  
  
2.  <span data-ttu-id="624c7-116">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="624c7-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="624c7-117">더하기 기호를 클릭하여 **정책 관리**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="624c7-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="624c7-118">더하기 기호를 클릭하여 **정책** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="624c7-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="624c7-119">평가할 정책을 마우스 오른쪽 단추로 클릭하고 **평가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="624c7-119">Right-click the policy that you want to evaluate and select **Evaluate**.</span></span>  
  
6.  <span data-ttu-id="624c7-120">**평가 결과**  대화 상자에 정책 평가의 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="624c7-120">In the **Evaluate Results**  dialog box, you see the results of the policy evaluation.</span></span> <span data-ttu-id="624c7-121">정책을 따르지 않고 정책 기반 관리로 다시 구성할 수 있는 속성이 있는 대상의 경우 **적용**을 클릭하여 준수를 강제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="624c7-121">For targets that do not comply with the policy and have properties that can be reconfigured by Policy-Based Management, you can enforce compliance by clicking **Apply**.</span></span> <span data-ttu-id="624c7-122">**정책 평가** 대화 상자에서 사용할 수 있는 옵션에 대한 자세한 내용은 [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md) 및 [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="624c7-122">For more information on the available options in the **Evaluate Policies** dialog box, see [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md) and [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md).</span></span>  
  
7.  <span data-ttu-id="624c7-123">완료되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="624c7-123">When finished, click **Close**.</span></span>  
  
  
