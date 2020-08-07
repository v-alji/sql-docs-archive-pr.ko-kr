---
title: 정책 평가 대화 상자, 정책 선택 페이지 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.runnow.f1
ms.assetid: 20075fbe-0b48-42c8-b747-690f1aa23dcf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f68a1ccc7873b6a05d2641ddaa87e8d5b0e5c6d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729359"
---
# <a name="evaluate-policies-dialog-box-policy-selection-page"></a><span data-ttu-id="04b39-102">정책 평가 대화 상자, 정책 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="04b39-102">Evaluate Policies Dialog Box, Policy Selection Page</span></span>
  <span data-ttu-id="04b39-103">이 대화 상자를 사용하여 정책 기반 관리 정책을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-103">Use this dialog box to evaluate Policy-Based Management policies.</span></span> <span data-ttu-id="04b39-104">**평가 결과** 페이지를 선택하면 정책을 준수하지 않는 대상 집합의 항목에 정책을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-104">By selecting the **Evaluation Results** page, you can apply policies to the items in a target set that do not comply with the policies.</span></span>  
  
## <a name="options"></a><span data-ttu-id="04b39-105">옵션</span><span class="sxs-lookup"><span data-stu-id="04b39-105">Options</span></span>  
 <span data-ttu-id="04b39-106">**원본**</span><span class="sxs-lookup"><span data-stu-id="04b39-106">**Source**</span></span>  
 <span data-ttu-id="04b39-107">정책의 원본을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-107">Specifies the source of the policies.</span></span> <span data-ttu-id="04b39-108">원본을 변경하려면 찾아보기 단추 (**...**)를 클릭하여 **원본 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-108">To change the source, click the Browse (**...**) button to open the **Select Source** dialog box.</span></span>  
  
 <span data-ttu-id="04b39-109">**파일**</span><span class="sxs-lookup"><span data-stu-id="04b39-109">**Files**</span></span>  
 <span data-ttu-id="04b39-110">정책 기반 관리 정책이 포함된 파일의 경로를 입력하거나 찾아보기 단추(**...**)를 사용하여 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-110">Type the path of a file that contains a Policy-Based Management policy, or use the Browse (**...**) button to select the file.</span></span>  
  
 <span data-ttu-id="04b39-111">**Server**</span><span class="sxs-lookup"><span data-stu-id="04b39-111">**Server**</span></span>  
 <span data-ttu-id="04b39-112">원하는 정책이 포함된 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-112">Select to connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that contains the policy that you want.</span></span>  
  
 <span data-ttu-id="04b39-113">**정책: 정책**</span><span class="sxs-lookup"><span data-stu-id="04b39-113">**Policies: Policy**</span></span>  
 <span data-ttu-id="04b39-114">지정된 정책에 대한 정책 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-114">Click to open the policy dialog box for the specified policy.</span></span>  
  
 <span data-ttu-id="04b39-115">**정책: 범주**</span><span class="sxs-lookup"><span data-stu-id="04b39-115">**Policies: Category**</span></span>  
 <span data-ttu-id="04b39-116">정책의 범주입니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-116">The category of the policy.</span></span> <span data-ttu-id="04b39-117">이 부분은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-117">This box is read-only.</span></span>  
  
 <span data-ttu-id="04b39-118">**정책: 패싯**</span><span class="sxs-lookup"><span data-stu-id="04b39-118">**Policies: Facet**</span></span>  
 <span data-ttu-id="04b39-119">정책에 의해 구현되는 패싯입니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-119">The facet implemented by the policy.</span></span> <span data-ttu-id="04b39-120">이 부분은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-120">This box is read-only.</span></span>  
  
 <span data-ttu-id="04b39-121">**구하려는**</span><span class="sxs-lookup"><span data-stu-id="04b39-121">**Evaluate**</span></span>  
 <span data-ttu-id="04b39-122">평가 모드에서 정책을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-122">Runs the policy in evaluation mode.</span></span> <span data-ttu-id="04b39-123">이렇게 하면 대상 집합에 대한 준수 보고서가 생성되지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 다시 구성되거나 앞으로 정책이 준수되도록 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-123">This generates a compliance report for the target set but does not reconfigure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or enforce future compliance.</span></span>  
  
## <a name="possible-errors"></a><span data-ttu-id="04b39-124">가능한 오류</span><span class="sxs-lookup"><span data-stu-id="04b39-124">Possible Errors</span></span>  
  
-   <span data-ttu-id="04b39-125">**대상이 없습니다.**</span><span class="sxs-lookup"><span data-stu-id="04b39-125">**No targets found**</span></span>  
  
     <span data-ttu-id="04b39-126">다음 이유 중 하나로 인해 대상 집합이 비어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-126">The target set could be empty due to any of the following reasons:</span></span>  
  
    -   <span data-ttu-id="04b39-127">정책으로 지정된 유형의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대상이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-127">There are no targets on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] of the type specified by the policy.</span></span>  
  
    -   <span data-ttu-id="04b39-128">서버 제한으로 인해 대상이 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 제외되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-128">The server restriction might exclude the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contains the target.</span></span>  
  
    -   <span data-ttu-id="04b39-129">정책이 데이터베이스의 개체(예: 테이블, 뷰 또는 사용자)에 있는 경우 데이터베이스는 정책의 범주를 구독하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-129">If the policy is on an object in a database (for example a table, view, or user) the database might not subscribe to the category of the policy.</span></span>  
  
    -   <span data-ttu-id="04b39-130">대상 집합 필터로 인해 이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 모든 대상이 제외되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-130">The target-set filter might exclude all targets on this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="04b39-131">대상 서버 유형은 정책을 평가하는 서버 유형과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-131">The target server type is different from the server type on which the policy is evaluated.</span></span> <span data-ttu-id="04b39-132">예를 들어 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 대해 만든 정책을 평가하면 빈 대상 집합을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04b39-132">For example, in the [!INCLUDE[ssDE](../../includes/ssde-md.md)], if you try to evaluate a policy that has been created for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you will receive an empty target set</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b39-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04b39-133">See Also</span></span>  
 <span data-ttu-id="04b39-134">[정책 기반 관리를 사용 하 여 서버 관리](administer-servers-by-using-policy-based-management.md) </span><span class="sxs-lookup"><span data-stu-id="04b39-134">[Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md) </span></span>  
 [<span data-ttu-id="04b39-135">정책 평가 대화 상자, 평가 결과 페이지</span><span class="sxs-lookup"><span data-stu-id="04b39-135">Evaluate Policies Dialog Box, Evaluation Results Page</span></span>](evaluate-policies-dialog-box-evaluation-results-page.md)  
  
  
