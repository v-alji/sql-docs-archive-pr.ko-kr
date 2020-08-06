---
title: 코드 자동 생성(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9c12e000b2f6ff2ecad07bd62f8c6c05afa36f82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638889"
---
# <a name="automatic-code-creation-master-data-services"></a><span data-ttu-id="e536a-102">코드 자동 생성(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e536a-102">Automatic Code Creation (Master Data Services)</span></span>
  <span data-ttu-id="e536a-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 코드 특성 또는 기타 숫자 특성에 대해 숫자 값을 자동으로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], numeric values can be automatically generated for the Code attribute, or for any other numeric attribute.</span></span> <span data-ttu-id="e536a-104">코드가 자동으로 생성될 때 코드에 다른 값을 입력할 수 없는 것은 아니지만 초기 값이 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-104">When codes are generated automatically, you are not prevented from entering other values for codes; rather an initial value is automatically set.</span></span>  
  
## <a name="generating-code-values"></a><span data-ttu-id="e536a-105">코드 값 생성</span><span class="sxs-lookup"><span data-stu-id="e536a-105">Generating Code Values</span></span>  
 <span data-ttu-id="e536a-106">관리자는 연결된 엔터티의 속성을 편집하여 코드 특성에 대한 자동 생성 값을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-106">Administrators can configure automatically-generated values for the Code attribute by editing the associated entity's properties.</span></span> <span data-ttu-id="e536a-107">관리자가 초기 값을 지정할 수 있으며 이후의 각 값은 1씩 증가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-107">They can specify an initial value, and each subsequent value is increased by one.</span></span>  
  
 <span data-ttu-id="e536a-108">도구 중 하나를 사용하거나 준비 프로세스를 사용하여 코드 값을 MDS에 입력할 때 코드 값을 비워 둘 수 있으며 이 경우 코드 값이 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-108">When you enter Code values into MDS, either in one of the tools or by using the staging process, you can leave the Code value blank and a Code value will be automatically generated.</span></span> <span data-ttu-id="e536a-109">또는 원하는 코드 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-109">Or you can specify a Code value of your choice.</span></span>  
  
## <a name="generating-other-attribute-values"></a><span data-ttu-id="e536a-110">다른 특성 값 생성</span><span class="sxs-lookup"><span data-stu-id="e536a-110">Generating Other Attribute Values</span></span>  
 <span data-ttu-id="e536a-111">관리자는 비즈니스 규칙을 만들어 코드 외의 특성 값을 자동으로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-111">Administrators can automatically generate values for attributes other than Code by creating business rules.</span></span> <span data-ttu-id="e536a-112">초기 값을 지정할 수 있으며 이후의 각 값이 증가되는 수치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-112">They can specify an initial value, and specify the number each subsequent value is incremented by.</span></span>  
  
 <span data-ttu-id="e536a-113">도구 중 하나를 사용하거나 준비 프로세스를 사용하여 특성 값을 MDS에 입력할 때 특성 값을 비워 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-113">When you enter attribute values into MDS, either in one of the tools or by using the staging process, you can leave the attribute value blank.</span></span> <span data-ttu-id="e536a-114">비즈니스 규칙이 적용되면 가장 높은 기존 값을 기반으로 값이 증가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-114">When business rules are applied, the values will be incremented based on the highest existing value.</span></span> <span data-ttu-id="e536a-115">예를 들어 규칙이 "1에서 시작하고 4씩 증가하는 생성된 값을 특성 기본값으로 설정"이고 특성의 가장 높은 현재 값이 700인 경우 추가되는 다음 멤버의 값은 704가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-115">For example, if your rule is "Default attribute to a generated value that starts at 1 and increments by 4" and the highest current value for the attribute is 700, the value for the next member that's added will be 704.</span></span>  
  
## <a name="deleting-automatically-generated-values"></a><span data-ttu-id="e536a-116">자동으로 생성된 값 삭제</span><span class="sxs-lookup"><span data-stu-id="e536a-116">Deleting Automatically Generated Values</span></span>  
 <span data-ttu-id="e536a-117">관리자가 코드 특성에 대해 자동 생성 값을 설정한 후 사용자가 다시 사용하려는 코드 값이 포함된 멤버를 실수로 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-117">After an administrator enables automatically generated values for the Code attribute, users may accidentally delete a member that had a Code value they want to reuse.</span></span> <span data-ttu-id="e536a-118">"삭제 된 멤버에서 이미 멤버 코드를 사용 하 고 있습니다." 라는 오류 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-118">The error message "The member code is already used by a member that was deleted" will be displayed.</span></span> <span data-ttu-id="e536a-119">가능한 해결 방법으로 다음 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-119">There are two possible solutions:</span></span>  
  
-   <span data-ttu-id="e536a-120">**버전 관리** 기능 영역에서 관리자가 멤버가 삭제될 때 발생한 트랜잭션을 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-120">In the **Version Management** functional area, an administrator can reverse the transaction that occurred when the member was deleted.</span></span> <span data-ttu-id="e536a-121">그러나이는 계층 및 컬렉션에서 이전 멤버의 모든 특성 및 멤버 자격이 복원 됨을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-121">However, this means that all of the former member's attributes and membership in hierarchies and collections is restored.</span></span> <span data-ttu-id="e536a-122">자세한 내용은 [역방향 a Transaction &#40;MDS(Master Data Services)&#41;](reverse-a-transaction-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e536a-122">For more information, see [Reverse a Transaction &#40;Master Data Services&#41;](reverse-a-transaction-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="e536a-123">관리자는 준비 프로세스를 사용하여 멤버를 영구적으로 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e536a-123">An administrator can use the staging process to permanently delete the member.</span></span> <span data-ttu-id="e536a-124">자세한 내용은 [준비 프로세스를 사용 하 여 멤버 비활성화 또는 삭제 &#40;MDS(Master Data Services)&#41;](add-update-and-delete-data-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e536a-124">For more information, see [Deactivate or Delete Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e536a-125">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e536a-125">Related Tasks</span></span>  
  
|<span data-ttu-id="e536a-126">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="e536a-126">Task Description</span></span>|<span data-ttu-id="e536a-127">항목</span><span class="sxs-lookup"><span data-stu-id="e536a-127">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="e536a-128">코드 특성 값 자동 생성</span><span class="sxs-lookup"><span data-stu-id="e536a-128">Automatically generate values for the Code attribute.</span></span>|[<span data-ttu-id="e536a-129">코드 특성 값 자동 생성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e536a-129">Automatically Generate Code Attribute Values &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|<span data-ttu-id="e536a-130">다른 특성 값 자동 생성</span><span class="sxs-lookup"><span data-stu-id="e536a-130">Automatically generate values for other attributes.</span></span>|[<span data-ttu-id="e536a-131">코드 외의 특성 값 자동 생성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e536a-131">Automatically Generate Attribute Values Other Than Code &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="e536a-132">관련 내용</span><span class="sxs-lookup"><span data-stu-id="e536a-132">Related Content</span></span>  
  
-   [<span data-ttu-id="e536a-133">MDS(Master Data Services) 개요</span><span class="sxs-lookup"><span data-stu-id="e536a-133">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
-   [<span data-ttu-id="e536a-134">비즈니스 규칙&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e536a-134">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="e536a-135">엔터티&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e536a-135">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)  
  
  
