---
title: 유효성 검사 페이지 (AlwaysOn 가용성 그룹 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.newagwizard.validation.f1
- sql12.swb.addreplicawizard.validation.f1
- sql12.swb.adddatabasewizard.validation.f1
helpviewer_keywords:
- ', listeners'
ms.assetid: c8971556-240c-491a-bc86-9cc72f71a3dd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f2010074a357932f8af7358a05ee6ed16f5c0881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646659"
---
# <a name="validation-page-alwayson-availability-group-wizards"></a><span data-ttu-id="97d19-102">유효성 검사 페이지(AlwaysOn 가용성 그룹 마법사)</span><span class="sxs-lookup"><span data-stu-id="97d19-102">Validation Page (AlwaysOn Availability Group Wizards)</span></span>
  <span data-ttu-id="97d19-103">이 도움말 항목에서는 **유효성 검사** 페이지의 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-103">This help topic describes the options of the **Validation** page.</span></span> <span data-ttu-id="97d19-104">이 항목은 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]의 [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)], [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 및 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-104">This topic applies to the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)], and [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="97d19-105">이 페이지를 사용하여 사용자 환경에서 마법사의 이전 페이지에서 선택한 모든 구성 항목을 지원하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-105">Use this page to validate that your environment supports all the configuration choices you made on previous pages of the wizard.</span></span>  
  
##  <a name="validation-page-options"></a><a name="PageOptions"></a><span data-ttu-id="97d19-106">유효성 검사 페이지 옵션</span><span class="sxs-lookup"><span data-stu-id="97d19-106">Validation Page Options</span></span>  
 <span data-ttu-id="97d19-107">**가용성 그룹의 유효성 검사 결과입니다.**</span><span class="sxs-lookup"><span data-stu-id="97d19-107">**Results of availability group validation.**</span></span>  
 <span data-ttu-id="97d19-108">이 표는 각 완료된 유효성 검사 단계의 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-108">This grid displays the results of each completed validation step.</span></span> <span data-ttu-id="97d19-109">표 열은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-109">The grid columns are as follows:</span></span>  
  
 <span data-ttu-id="97d19-110">**이름**</span><span class="sxs-lookup"><span data-stu-id="97d19-110">**Name**</span></span>  
 <span data-ttu-id="97d19-111">특정 단계를 설명하는 문구를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-111">Displays a phrase that describes a specific step.</span></span>  
  
 <span data-ttu-id="97d19-112">**결과**</span><span class="sxs-lookup"><span data-stu-id="97d19-112">**Result**</span></span>  
 <span data-ttu-id="97d19-113">다음 하이퍼링크 텍스트 중 하나를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-113">Displays one of the following hyperlink texts.</span></span> <span data-ttu-id="97d19-114">지정된 유효성 검사 단계의 결과에 대한 자세한 내용을 보려면 하이퍼링크를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="97d19-114">For more information about the result of given validation step, click the hyperlink.</span></span>  
  
|<span data-ttu-id="97d19-115">결과</span><span class="sxs-lookup"><span data-stu-id="97d19-115">Result</span></span>|<span data-ttu-id="97d19-116">Description</span><span class="sxs-lookup"><span data-stu-id="97d19-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="97d19-117">**오류**</span><span class="sxs-lookup"><span data-stu-id="97d19-117">**Error**</span></span>|<span data-ttu-id="97d19-118">유효성 검사 단계가 실패했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-118">Indicates that the validation step failed.</span></span> <span data-ttu-id="97d19-119">오류 메시지를 보려면 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-119">Click the link to view the error message.</span></span>|  
|<span data-ttu-id="97d19-120">**생략**</span><span class="sxs-lookup"><span data-stu-id="97d19-120">**Skipped**</span></span>|<span data-ttu-id="97d19-121">선택 항목에 필요하지 않아 유효성 검사 단계를 건너뛰었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-121">Indicates that the validation step was skipped because it is not required by your selections.</span></span> <span data-ttu-id="97d19-122">단계를 건너뛴 이유를 보려면 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-122">Click the link to view the reason that a step was skipped.</span></span>|  
|<span data-ttu-id="97d19-123">**Success**</span><span class="sxs-lookup"><span data-stu-id="97d19-123">**Success**</span></span>|<span data-ttu-id="97d19-124">유효성 검사 단계가 완료되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-124">Indicates that the validation step completed successfully</span></span>|  
|<span data-ttu-id="97d19-125">**경고**</span><span class="sxs-lookup"><span data-stu-id="97d19-125">**Warning**</span></span>|<span data-ttu-id="97d19-126">가용성 그룹 구성에 대한 잠재적 문제를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-126">Indicates a potential issue with the availability group configuration.</span></span>  <span data-ttu-id="97d19-127">경고 메시지를 보려면 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-127">Click the link to view the warning message.</span></span>|  
  
 <span data-ttu-id="97d19-128">**유효성 검사 다시 실행**</span><span class="sxs-lookup"><span data-stu-id="97d19-128">**Re-run Validation**</span></span>  
 <span data-ttu-id="97d19-129">유효성 검사 오류에 응답하여 마법사 외부에서 변경할 경우 유효성 검사 단계를 반복하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97d19-129">Click to repeat the validation steps if you make a change outside of the wizard in response to a validation error.</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="97d19-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="97d19-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="97d19-131">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="97d19-131">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="97d19-132">가용성 그룹에 복제본 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="97d19-132">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="97d19-133">가용성 그룹에 데이터베이스 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="97d19-133">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
 
  
## <a name="see-also"></a><span data-ttu-id="97d19-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97d19-134">See Also</span></span>  
 [<span data-ttu-id="97d19-135">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="97d19-135">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
