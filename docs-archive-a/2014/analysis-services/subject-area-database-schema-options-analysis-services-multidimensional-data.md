---
title: 주제 영역 데이터베이스 스키마 옵션 (스키마 생성 마법사) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.schemagenwizard.subjectareaschemaopts.f1
ms.assetid: 4c109bb8-e19d-412b-908f-bfdd7f872439
author: minewiskan
ms.author: owend
ms.openlocfilehash: 98460332478d02de823addcd113fb9c1e87d6958
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649713"
---
# <a name="subject-area-database-schema-options-schema-generation-wizard-analysis-services---multidimensional-data"></a><span data-ttu-id="5a8ed-102">주제 영역 데이터베이스 스키마 옵션(스키마 생성 마법사)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="5a8ed-102">Subject Area Database Schema Options (Schema Generation Wizard) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="5a8ed-103">**주제 영역 데이터베이스 스키마 옵션** 페이지를 사용하여 스키마 생성 방법을 제어하고 데이터 유지 방법을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-103">Use the **Subject Area Database Schema Options** page to control how the schema is generated, as well as to define how data is preserved.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5a8ed-104">옵션</span><span class="sxs-lookup"><span data-stu-id="5a8ed-104">Options</span></span>  
 <span data-ttu-id="5a8ed-105">**소유 스키마**</span><span class="sxs-lookup"><span data-stu-id="5a8ed-105">**Owning schema**</span></span>  
 <span data-ttu-id="5a8ed-106">새 주제 영역 데이터베이스 내 스키마의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-106">Specifies the name of the schema within the new subject area database.</span></span>  
  
 <span data-ttu-id="5a8ed-107">**차원 테이블에 기본 키 만들기**</span><span class="sxs-lookup"><span data-stu-id="5a8ed-107">**Create primary keys on dimension tables**</span></span>  
 <span data-ttu-id="5a8ed-108">생성된 스키마의 차원 테이블에 기본 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-108">Creates primary keys on the dimension tables in the generated schema.</span></span> <span data-ttu-id="5a8ed-109">이 옵션을 선택하지 않으면 인덱스가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-109">No index is generated if you do not select this option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5a8ed-110">이 옵션을 선택하지 않으면 참조 무결성이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-110">If you do not select this option, referential integrity is enforced.</span></span>  
  
 <span data-ttu-id="5a8ed-111">**인덱스 만들기**</span><span class="sxs-lookup"><span data-stu-id="5a8ed-111">**Create indexes**</span></span>  
 <span data-ttu-id="5a8ed-112">생성된 스키마의 외래 키 열에 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-112">Creates indexes on foreign key columns in the generated schema.</span></span>  
  
 <span data-ttu-id="5a8ed-113">**참조 무결성 적용**</span><span class="sxs-lookup"><span data-stu-id="5a8ed-113">**Enforce referential integrity**</span></span>  
 <span data-ttu-id="5a8ed-114">생성된 스키마 내에 참조 무결성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-114">Enforces referential integrity within the generated schema.</span></span> <span data-ttu-id="5a8ed-115">이 옵션을 선택하지 않으면 관계가 생성되지만 적용되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-115">If you do not select this option, relationships are created but not enforced.</span></span>  
  
 <span data-ttu-id="5a8ed-116">**다시 생성 시 데이터 유지**</span><span class="sxs-lookup"><span data-stu-id="5a8ed-116">**Preserve data on regeneration**</span></span>  
 <span data-ttu-id="5a8ed-117">마법사가 완료될 때 주제 영역 데이터베이스에 데이터를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-117">Retains data in the subject area database when the wizard finishes.</span></span> <span data-ttu-id="5a8ed-118">이 옵션을 선택하지 않으면 주제 영역 데이터베이스의 모든 데이터가 경고 없이 지워질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-118">If you do not select this option, all the data in the subject area database may be erased without warning.</span></span>  
  
 <span data-ttu-id="5a8ed-119">**시간 테이블 채우기**</span><span class="sxs-lookup"><span data-stu-id="5a8ed-119">**Populate time table(s)**</span></span>  
 <span data-ttu-id="5a8ed-120">마법사에서 시간 테이블을 채우는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-120">Specifies how the wizard populates the time tables.</span></span> <span data-ttu-id="5a8ed-121">다음 표에서는 이 옵션에 사용할 수 있는 값에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-121">The following table describes the possible values for this option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5a8ed-122">이 옵션은 프로젝트 모드에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 를 사용하여 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 프로젝트에서 스키마 생성 마법사를 호출한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-122">This option is enabled only if Schema Generation Wizard is called from an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] in project mode.</span></span>  
  
|<span data-ttu-id="5a8ed-123">값</span><span class="sxs-lookup"><span data-stu-id="5a8ed-123">Value</span></span>|<span data-ttu-id="5a8ed-124">Description</span><span class="sxs-lookup"><span data-stu-id="5a8ed-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5a8ed-125">채우기</span><span class="sxs-lookup"><span data-stu-id="5a8ed-125">Populate</span></span>|<span data-ttu-id="5a8ed-126">주제 영역 시간 테이블을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-126">The subject area time tables are populated.</span></span>|  
|<span data-ttu-id="5a8ed-127">채우지 않음</span><span class="sxs-lookup"><span data-stu-id="5a8ed-127">Do not populate</span></span>|<span data-ttu-id="5a8ed-128">주제 영역 시간 테이블을 채우지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-128">The subject area time tables are not populated.</span></span>|  
|<span data-ttu-id="5a8ed-129">비어 있는 경우에만 채우기</span><span class="sxs-lookup"><span data-stu-id="5a8ed-129">Populate only if empty</span></span>|<span data-ttu-id="5a8ed-130">비어 있는 경우에만 주제 영역 시간 테이블을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="5a8ed-130">The subject area time tables are populated only if they are empty.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a8ed-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5a8ed-131">See Also</span></span>  
 [<span data-ttu-id="5a8ed-132">스키마 생성 마법사 F1 도움말 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="5a8ed-132">Schema Generation Wizard F1 Help &#40;Analysis Services - Multidimensional Data&#41;</span></span>](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md)  
  
  
