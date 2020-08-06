---
title: 어셈블리 속성 대화 상자 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.assemblyproperties.f1
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
author: minewiskan
ms.author: owend
ms.openlocfilehash: b9fdd506da42c5088b173db0981b5df94f91e5f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648179"
---
# <a name="assembly-properties-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="95bbf-102">어셈블리 속성 대화 상자(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="95bbf-102">Assembly Properties Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="95bbf-103">**의** 어셈블리 속성 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스의 어셈블리 참조 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-103">Use the **Assembly Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the properties of an assembly reference in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="95bbf-104">**개체 탐색기** 에서 어셈블리를 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택하여 **어셈블리 속성**대화 상자를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-104">You can display the **Assembly Properties** dialog box by right-clicking an assembly in **Object Explorer** and selecting **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="95bbf-105">옵션</span><span class="sxs-lookup"><span data-stu-id="95bbf-105">Options</span></span>  
  
|<span data-ttu-id="95bbf-106">용어</span><span class="sxs-lookup"><span data-stu-id="95bbf-106">Term</span></span>|<span data-ttu-id="95bbf-107">정의</span><span class="sxs-lookup"><span data-stu-id="95bbf-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="95bbf-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="95bbf-108">**Name**</span></span>|<span data-ttu-id="95bbf-109">어셈블리 참조의 이름을 변경하려면 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-109">Type to change the name of the assembly reference.</span></span><br /><br /> <span data-ttu-id="95bbf-110">참고: 이 값을 변경하면 어셈블리 참조에서 참조하는 어셈블리 이름은 변경되지 않지만 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스 또는 데이터베이스에서 해당 어셈블리 참조를 참조할 때 사용하는 이름이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-110">Note: Changing this value does not change the name of the assembly referred to by the assembly reference, but instead changes the name used the by the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or database when referring to the assembly reference.</span></span>|  
|<span data-ttu-id="95bbf-111">**ID**</span><span class="sxs-lookup"><span data-stu-id="95bbf-111">**ID**</span></span>|<span data-ttu-id="95bbf-112">어셈블리 참조에서 참조하는 어셈블리의 식별자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-112">Displays the identifier of the assembly referred to by the assembly reference.</span></span>|  
|<span data-ttu-id="95bbf-113">**설명**</span><span class="sxs-lookup"><span data-stu-id="95bbf-113">**Description**</span></span>|<span data-ttu-id="95bbf-114">어셈블리 참조에 대한 설명을 변경하려면 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-114">Type to change the description of the assembly reference.</span></span>|  
|<span data-ttu-id="95bbf-115">**생성된 타임스탬프**</span><span class="sxs-lookup"><span data-stu-id="95bbf-115">**Create Timestamp**</span></span>|<span data-ttu-id="95bbf-116">어셈블리 참조가 생성된 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-116">Displays the date and time the assembly reference was created.</span></span>|  
|<span data-ttu-id="95bbf-117">**최종 스키마 업데이트**</span><span class="sxs-lookup"><span data-stu-id="95bbf-117">**Last Schema Update**</span></span>|<span data-ttu-id="95bbf-118">어셈블리 참조의 메타데이터가 마지막으로 업데이트된 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-118">Displays the date and time the metadata for the assembly reference was last updated.</span></span>|  
|<span data-ttu-id="95bbf-119">**형식**</span><span class="sxs-lookup"><span data-stu-id="95bbf-119">**Type**</span></span>|<span data-ttu-id="95bbf-120">어셈블리 참조의 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-120">Displays the type of the assembly reference.</span></span> <span data-ttu-id="95bbf-121">다음과 같은 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-121">The following values are displayed:</span></span><br /><br /> <span data-ttu-id="95bbf-122">**.Net 어셈블리**: 어셈블리 참조는 .NET Framework 어셈블리를 참조 합니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="95bbf-122">**.NET Assembly**: The assembly reference refers to a [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework assembly.</span></span><br /><br /> <span data-ttu-id="95bbf-123">**COM DLL**: 어셈블리 참조는 com 라이브러리를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-123">**COM DLL**: The assembly reference refers to a COM library.</span></span>|  
|<span data-ttu-id="95bbf-124">**원본**</span><span class="sxs-lookup"><span data-stu-id="95bbf-124">**Source**</span></span>|<span data-ttu-id="95bbf-125">어셈블리 참조의 원본을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-125">Displays the source of the assembly reference.</span></span> <span data-ttu-id="95bbf-126">이 속성에는 일반적으로 어셈블리 참조에서 참조하는 어셈블리의 전체 경로와 파일 이름이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-126">This property typically contains the full path and file name of the assembly referred to by the assembly reference.</span></span>|  
|<span data-ttu-id="95bbf-127">**권한 집합**</span><span class="sxs-lookup"><span data-stu-id="95bbf-127">**Permission Set**</span></span>|<span data-ttu-id="95bbf-128">어셈블리 참조에 대한 액세스 권한을 결정하는 데 사용되는 권한 집합을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-128">Select the permission set used to determine access to the assembly reference.</span></span> <span data-ttu-id="95bbf-129">이 속성에 사용할 수 있는 값에 대한 자세한 내용은 <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="95bbf-129">For more information about the available values for this property, see <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>.</span></span>|  
|<span data-ttu-id="95bbf-130">**가장 정보**</span><span class="sxs-lookup"><span data-stu-id="95bbf-130">**Impersonation Info**</span></span>|<span data-ttu-id="95bbf-131">어셈블리 참조에 액세스할 때 사용할 가장 정보를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="95bbf-131">Select the impersonation information to use when accessing the assembly reference.</span></span> <span data-ttu-id="95bbf-132">이 속성에 사용할 수 있는 값에 대한 자세한 내용은 [ImpersonationInfo 요소&#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="95bbf-132">For more information about the available values for this property, see [ImpersonationInfo Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95bbf-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95bbf-133">See Also</span></span>  
 <span data-ttu-id="95bbf-134">[Analysis Services 디자이너 및 대화 상자 &#40;다차원 데이터&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="95bbf-134">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="95bbf-135">다차원 모델 어셈블리 관리</span><span class="sxs-lookup"><span data-stu-id="95bbf-135">Multidimensional Model Assemblies Management</span></span>](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
