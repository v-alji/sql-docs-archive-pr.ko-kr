---
title: 결과 자세히 보기 대화 상자 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.results.f1
- sql12.swb.dmf.policy.resultdetails.f1
ms.assetid: 366f0ff8-722a-40a9-934f-854147e4933d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1c4d669fb1546d27eb8b6ae78e0de8dea5975f24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740863"
---
# <a name="results-detailed-view-dialog-box"></a><span data-ttu-id="5246f-102">결과 자세히 보기 대화 상자</span><span class="sxs-lookup"><span data-stu-id="5246f-102">Results Detailed View Dialog Box</span></span>
  <span data-ttu-id="5246f-103">**정책 실행** 대화 상자를 사용하여 정책을 실행하고 **실행**을 클릭하면 정책 평가 결과가 이 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5246f-103">This dialog box shows the results of policy evaluation after you have run a policy by using the **Evaluate Policies** dialog box and clicked **Evaluate**.</span></span> <span data-ttu-id="5246f-104">이 대화 상자는 읽기 전용이며 속성 식에서 실패할 수 있는 부분을 이해하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5246f-104">This dialog box is read-only, and helps you understand which part of a property expression might be failing.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5246f-105">옵션</span><span class="sxs-lookup"><span data-stu-id="5246f-105">Options</span></span>  
 <span data-ttu-id="5246f-106">**AndOr**</span><span class="sxs-lookup"><span data-stu-id="5246f-106">**AndOr**</span></span>  
 <span data-ttu-id="5246f-107">둘 이상의 속성 식이 있는 경우 속성 식이 누적되는지, 아니면 대체되는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5246f-107">When more than one property expression is present, indicates whether the property expressions are cumulative or alternative.</span></span>  
  
 <span data-ttu-id="5246f-108">**결과**</span><span class="sxs-lookup"><span data-stu-id="5246f-108">**Result**</span></span>  
 <span data-ttu-id="5246f-109">속성 식의 성공 또는 실패를 나타내는 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="5246f-109">Icon that represents the success or failure of the property expression.</span></span>  
  
 <span data-ttu-id="5246f-110">**필드**</span><span class="sxs-lookup"><span data-stu-id="5246f-110">**Field**</span></span>  
 <span data-ttu-id="5246f-111">모델링되는 패싯의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="5246f-111">The property of the facet that is being modeled.</span></span>  
  
 <span data-ttu-id="5246f-112">**연산자**</span><span class="sxs-lookup"><span data-stu-id="5246f-112">**Operator**</span></span>  
 <span data-ttu-id="5246f-113">식에 대한 연산자(예: **=** 또는 **Like**)입니다.</span><span class="sxs-lookup"><span data-stu-id="5246f-113">The operator for the expression, for example **=** or **Like**.</span></span>  
  
 <span data-ttu-id="5246f-114">**예상 값**</span><span class="sxs-lookup"><span data-stu-id="5246f-114">**Expected Value**</span></span>  
 <span data-ttu-id="5246f-115">속성 식이 성공하는 데 필요한 필드 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5246f-115">The value for the field that will cause the property expression to be successful.</span></span>  
  
 <span data-ttu-id="5246f-116">**실제 값**</span><span class="sxs-lookup"><span data-stu-id="5246f-116">**Actual Value**</span></span>  
 <span data-ttu-id="5246f-117">정책에 의해 검색된 필드 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5246f-117">The value for the field that was detected by the policy.</span></span>  
  
 <span data-ttu-id="5246f-118">**정책 설명**</span><span class="sxs-lookup"><span data-stu-id="5246f-118">**Policy description**</span></span>  
 <span data-ttu-id="5246f-119">정책에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="5246f-119">The description of the policy.</span></span>  
  
 <span data-ttu-id="5246f-120">**추가 도움말**</span><span class="sxs-lookup"><span data-stu-id="5246f-120">**Additional help**</span></span>  
 <span data-ttu-id="5246f-121">이 정책과 관련된 웹 페이지를 열려면 하이퍼링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5246f-121">Click the hyperlink to open a Web page that is related to this policy.</span></span> <span data-ttu-id="5246f-122">추가 도움말 하이퍼링크는 정책이 만들어질 때 구성되지만 비어 있거나 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5246f-122">The Additional Help hyperlink is configured when the policy is created and might be blank or unavailable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5246f-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5246f-123">See Also</span></span>  
 <span data-ttu-id="5246f-124">[정책 관리 노드&#40;개체 탐색기&#41;](../../ssms/object/object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="5246f-124">[Policy Management Node &#40;Object Explorer&#41;](../../ssms/object/object-explorer.md) </span></span>  
 [<span data-ttu-id="5246f-125">정책 기반 관리를 사용하여 서버 관리</span><span class="sxs-lookup"><span data-stu-id="5246f-125">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
