---
title: 보고서 속성 대화 상자, 참조 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10530"
- sql12.rtp.rptdesigner.reportproperties.references.f1
ms.assetid: 4639d368-9918-4bb1-9953-7a724ca78dea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b28ea0865d37bdc56054d6b23dc8c82d9279b08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733564"
---
# <a name="report-properties-dialog-box-references"></a><span data-ttu-id="df1eb-102">보고서 속성 대화 상자, 참조</span><span class="sxs-lookup"><span data-stu-id="df1eb-102">Report Properties Dialog Box, References</span></span>
  <span data-ttu-id="df1eb-103">**보고서 속성** 대화 상자의 **참조** 를 선택하여 보고서 정의의 식에 사용되는 사용자 지정 또는 다른 외부 어셈블리 및 사용자 지정 클래스 인스턴스에 대한 참조를 추가 또는 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-103">Select **References** on the **Report Properties** dialog box to add or remove references to custom or other external assemblies and custom class instances that are used by expressions in the report definition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="df1eb-104">옵션</span><span class="sxs-lookup"><span data-stu-id="df1eb-104">Options</span></span>  
 <span data-ttu-id="df1eb-105">**어셈블리 추가 또는 제거**</span><span class="sxs-lookup"><span data-stu-id="df1eb-105">**Add or remove assemblies**</span></span>  
 <span data-ttu-id="df1eb-106">보고서가 참조하는 어셈블리를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-106">Lists the assemblies that the report references.</span></span> <span data-ttu-id="df1eb-107">어셈블리는 보고서를 디자인하는 데 사용하는 도구가 설치되어 있는 컴퓨터 및 보고서 서버에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-107">The assembly must be available on the computer on which the tool you are using to design the report is installed and on the report server.</span></span> <span data-ttu-id="df1eb-108">참조의 이름은 **\<CodeModule>** Report Definition Language 파일 (.rdl)의 태그 내용과 정확 하 게 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-108">The name of the reference must match the contents of **\<CodeModule>** tags in the Report Definition Language (.rdl) file exactly.</span></span>  
  
 <span data-ttu-id="df1eb-109">**추가**</span><span class="sxs-lookup"><span data-stu-id="df1eb-109">**Add**</span></span>  
 <span data-ttu-id="df1eb-110">어셈블리를 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-110">Click to add an assembly.</span></span> <span data-ttu-id="df1eb-111">**열기** 대화 상자를 열고 보고서 처리 및 식 평가를 완료 하는 데 필요한 어셈블리를 선택 하려면 줄임표 (...) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-111">Click the ellipsis (...) button to open the **Open** dialog box and select the assemblies necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="df1eb-112">**삭제**</span><span class="sxs-lookup"><span data-stu-id="df1eb-112">**Delete**</span></span>  
 <span data-ttu-id="df1eb-113">목록에서 어셈블리 참조를 제거하려면 어셈블리 이름을 선택하고 **제거** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-113">To remove an assembly reference from the list, select the assembly name and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="df1eb-114">**클래스 추가 또는 제거**</span><span class="sxs-lookup"><span data-stu-id="df1eb-114">**Add or remove classes**</span></span>  
 <span data-ttu-id="df1eb-115">보고서에 사용되는 클래스 인스턴스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-115">Lists the class instances that are used by the report.</span></span> <span data-ttu-id="df1eb-116">클래스 목록은 인스턴스 기반 멤버만 사용할 수 있고 정적 멤버는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-116">The class list is used only by instance-based members, not static members.</span></span>  
  
 <span data-ttu-id="df1eb-117">**추가**</span><span class="sxs-lookup"><span data-stu-id="df1eb-117">**Add**</span></span>  
 <span data-ttu-id="df1eb-118">클래스 참조를 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-118">Click to add a class reference.</span></span> <span data-ttu-id="df1eb-119">**열기** 대화 상자를 열고 보고서 처리 및 식 평가를 완료 하는 데 필요한 클래스를 선택 하려면 줄임표 (...) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-119">Click the ellipsis (...) button to open the **Open** dialog box and select the classes necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="df1eb-120">**삭제**</span><span class="sxs-lookup"><span data-stu-id="df1eb-120">**Delete**</span></span>  
 <span data-ttu-id="df1eb-121">클래스 인스턴스를 삭제하려면 해당 인스턴스를 선택한 다음 **제거** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-121">To delete the class instance, select it and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="df1eb-122">**최대**</span><span class="sxs-lookup"><span data-stu-id="df1eb-122">**Up**</span></span>  
 <span data-ttu-id="df1eb-123">종속성이 있는 클래스의 경우 이 참조를 목록에서 더 위로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-123">For classes that have dependencies, you can move this reference higher in the list.</span></span>  
  
 <span data-ttu-id="df1eb-124">**아래로**</span><span class="sxs-lookup"><span data-stu-id="df1eb-124">**Down**</span></span>  
 <span data-ttu-id="df1eb-125">종속성이 있는 클래스의 경우 이 참조를 목록에서 더 아래로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df1eb-125">For classes that have dependencies, you can move this reference lower in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df1eb-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df1eb-126">See Also</span></span>  
 <span data-ttu-id="df1eb-127">[보고서 디자이너의 식에 포함된 사용자 지정 코드 및 어셈블리 참조&#40;SSRS&#41;](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="df1eb-127">[Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span></span>  
 <span data-ttu-id="df1eb-128">[보고서 및 그룹 변수 컬렉션 참조 &#40;보고서 작성기 및 SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="df1eb-128">[Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md) </span></span>  
 [<span data-ttu-id="df1eb-129">식 예&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="df1eb-129">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](report-design/expression-examples-report-builder-and-ssrs.md)  
  
  
