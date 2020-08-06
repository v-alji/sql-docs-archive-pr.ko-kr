---
title: 비즈니스 규칙에 대해 버전 유효성 검사(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- validating versions [Master Data Services]
- validating versions [Master Data Services], about validating versions
- versions [Master Data Services], validating
- business rules [Master Data Services], applying to all members
ms.assetid: 5aee7901-6d05-41d4-8bbb-c6f26791d1df
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 085fa071ca511c9d838c140547419bf87fb857bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650155"
---
# <a name="validate-a-version-against-business-rules-master-data-services"></a><span data-ttu-id="f148a-102">비즈니스 규칙에 대해 버전 유효성 검사(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f148a-102">Validate a Version against Business Rules (Master Data Services)</span></span>
  <span data-ttu-id="f148a-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 버전의 유효성을 검사하여 모델 버전의 모든 멤버에 비즈니스 규칙을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], validate a version to apply business rules to all members in the model version.</span></span>  
  
 <span data-ttu-id="f148a-104">이 절차는 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션을 사용하여 데이터의 유효성을 검사하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-104">This procedure explains how to use the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application to validate data.</span></span> <span data-ttu-id="f148a-105">MDS 데이터베이스에 대한 권한이 있는 경우 대신 저장 프로시저를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-105">If you have permission in the MDS database, you can use a stored procedure instead.</span></span> <span data-ttu-id="f148a-106">자세한 내용은 [유효성 검사 저장 프로시저&#40;Master Data Services&#41;](validation-stored-procedure-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f148a-106">For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](validation-stored-procedure-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f148a-107">모든 멤버가 유효성 검사를 통과해야 버전을 커밋할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-107">All members must pass validation before a version can be committed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f148a-108">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="f148a-108">Prerequisites</span></span>  
 <span data-ttu-id="f148a-109">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="f148a-109">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f148a-110">**버전 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-110">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="f148a-111">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-111">You must be a model administrator.</span></span> <span data-ttu-id="f148a-112">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f148a-112">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="f148a-113">버전의 상태가 **열림** 또는 **잠금**이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-113">The version's status must be **Open** or **Locked**.</span></span>  
  
-   <span data-ttu-id="f148a-114">**버전 유효성 검사** 페이지에 **유효성 검사 성공**상태가 아닌 멤버가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-114">On the **Validate Versions** page, members must exist with a status other than **Validation succeeded**.</span></span>  
  
### <a name="to-validate-a-version"></a><span data-ttu-id="f148a-115">버전의 유효성을 검사하려면</span><span class="sxs-lookup"><span data-stu-id="f148a-115">To validate a version</span></span>  
  
1.  <span data-ttu-id="f148a-116">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **버전 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-116">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="f148a-117">**버전 관리** 페이지의 메뉴 모음에서 **버전 유효성 검사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-117">On the **Manage Versions** page, from the menu bar, click **Validate Version**.</span></span>  
  
3.  <span data-ttu-id="f148a-118">**버전 유효성 검사** 페이지에서 유효성을 검사하려는 모델과 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-118">On the **Validate Versions** page, select the model and version you want to validate.</span></span>  
  
4.  <span data-ttu-id="f148a-119">**유효성 검사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-119">Click **Validate**.</span></span>  
  
5.  <span data-ttu-id="f148a-120">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-120">In the confirmation dialog box, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f148a-121">진행률 표시기가 더 이상 표시되지 않으면 버전의 유효성 검사가 완료된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f148a-121">When the progress indicator is no longer displayed, the version has finished validation.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f148a-122">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f148a-122">Next Steps</span></span>  
  
-   [<span data-ttu-id="f148a-123">버전 잠금&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f148a-123">Lock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/lock-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="f148a-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f148a-124">See Also</span></span>  
 <span data-ttu-id="f148a-125">[유효성 검사 상태 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/validation-statuses-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f148a-125">[Validation Statuses &#40;Master Data Services&#41;](../../2014/master-data-services/validation-statuses-master-data-services.md) </span></span>  
 <span data-ttu-id="f148a-126">[유효성 검사 저장 프로시저 &#40;MDS(Master Data Services)&#41;](validation-stored-procedure-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f148a-126">[Validation Stored Procedure &#40;Master Data Services&#41;](validation-stored-procedure-master-data-services.md) </span></span>  
 <span data-ttu-id="f148a-127">[버전 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f148a-127">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 <span data-ttu-id="f148a-128">[비즈니스 규칙 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f148a-128">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="f148a-129">비즈니스 규칙에 대해 특정 멤버 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f148a-129">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
  
