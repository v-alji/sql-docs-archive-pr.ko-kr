---
title: 보고서 속성 대화 상자, 참조 (보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10082"
ms.assetid: 3414c857-8ea6-4fc4-a6d5-b4883c039efa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2c28e9053a1c13f8d0e0b7b44f3b1a037976c318
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733571"
---
# <a name="report-properties-dialog-box-references-report-builder"></a><span data-ttu-id="4cd76-102">보고서 속성 대화 상자, 참조(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="4cd76-102">Report Properties Dialog Box, References (Report Builder)</span></span>
  <span data-ttu-id="4cd76-103">**보고서 속성** 대화 상자의 **참조** 를 선택하여 보고서 정의의 식에 사용되는 사용자 지정 또는 다른 외부 어셈블리 및 사용자 지정 클래스 인스턴스에 대한 참조를 추가 또는 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-103">Select **References** on the **Report Properties** dialog box to add or remove references to custom or other external assemblies and custom class instances that are used by expressions in the report definition.</span></span> <span data-ttu-id="4cd76-104">사용자 지정 어셈블리는 보고서 작성기의 로컬 모드에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-104">Custom assemblies are not supported in local mode in Report Builder.</span></span> <span data-ttu-id="4cd76-105">사용자 지정 어셈블리를 사용 하는 보고서를 작성 하려면에서 보고서 디자이너를 사용 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-105">To author reports that use custom assemblies, use Report Designer in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="4cd76-106">옵션</span><span class="sxs-lookup"><span data-stu-id="4cd76-106">Options</span></span>  
 <span data-ttu-id="4cd76-107">**어셈블리 추가 또는 제거**</span><span class="sxs-lookup"><span data-stu-id="4cd76-107">**Add or remove assemblies**</span></span>  
 <span data-ttu-id="4cd76-108">보고서가 참조하는 어셈블리를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-108">Lists the assemblies that the report references.</span></span> <span data-ttu-id="4cd76-109">어셈블리는 보고서를 디자인하는 데 사용하는 도구가 설치되어 있는 컴퓨터 및 보고서 서버에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-109">The assembly must be available on the computer on which the tool you are using to design the report is installed and on the report server.</span></span> <span data-ttu-id="4cd76-110">참조의 이름은 **\<CodeModule>** Report Definition Language 파일 (.rdl)의 태그 내용과 정확 하 게 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-110">The name of the reference must match the contents of **\<CodeModule>** tags in the Report Definition Language (.rdl) file exactly.</span></span>  
  
 <span data-ttu-id="4cd76-111">**추가**</span><span class="sxs-lookup"><span data-stu-id="4cd76-111">**Add**</span></span>  
 <span data-ttu-id="4cd76-112">어셈블리를 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-112">Click to add an assembly.</span></span> <span data-ttu-id="4cd76-113">**열기** 대화 상자를 열고 보고서 처리 및 식 평가를 완료 하는 데 필요한 어셈블리를 선택 하려면 줄임표 (...) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-113">Click the ellipsis (...) button to open the **Open** dialog box and select the assemblies necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="4cd76-114">**제거**</span><span class="sxs-lookup"><span data-stu-id="4cd76-114">**Remove**</span></span>  
 <span data-ttu-id="4cd76-115">목록에서 어셈블리 참조를 제거하려면 어셈블리 이름을 선택하고 **제거** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-115">To remove an assembly reference from the list, select the assembly name and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="4cd76-116">**클래스 추가 또는 제거**</span><span class="sxs-lookup"><span data-stu-id="4cd76-116">**Add or remove classes**</span></span>  
 <span data-ttu-id="4cd76-117">보고서에 사용되는 클래스 인스턴스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-117">Lists the class instances that are used by the report.</span></span> <span data-ttu-id="4cd76-118">클래스 목록은 인스턴스 기반 멤버만 사용할 수 있고 정적 멤버는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-118">The class list is used only by instance-based members, not static members.</span></span>  
  
 <span data-ttu-id="4cd76-119">**추가**</span><span class="sxs-lookup"><span data-stu-id="4cd76-119">**Add**</span></span>  
 <span data-ttu-id="4cd76-120">클래스 참조를 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-120">Click to add a class reference.</span></span> <span data-ttu-id="4cd76-121">**열기** 대화 상자를 열고 보고서 처리 및 식 평가를 완료 하는 데 필요한 클래스를 선택 하려면 줄임표 (...) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-121">Click the ellipsis (...) button to open the **Open** dialog box and select the classes necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="4cd76-122">**제거**</span><span class="sxs-lookup"><span data-stu-id="4cd76-122">**Remove**</span></span>  
 <span data-ttu-id="4cd76-123">클래스 인스턴스를 삭제하려면 해당 인스턴스를 선택한 다음 **제거** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-123">To delete the class instance, select it and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="4cd76-124">**최대**</span><span class="sxs-lookup"><span data-stu-id="4cd76-124">**Up**</span></span>  
 <span data-ttu-id="4cd76-125">종속성이 있는 클래스의 경우 이 참조를 목록에서 더 위로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-125">For classes that have dependencies, you can move this reference higher in the list.</span></span>  
  
 <span data-ttu-id="4cd76-126">**아래로**</span><span class="sxs-lookup"><span data-stu-id="4cd76-126">**Down**</span></span>  
 <span data-ttu-id="4cd76-127">종속성이 있는 클래스의 경우 이 참조를 목록에서 더 아래로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cd76-127">For classes that have dependencies, you can move this reference lower in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd76-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4cd76-128">See Also</span></span>  
 <span data-ttu-id="4cd76-129">[대화 상자, 창 및 마법사에 대 한 보고서 작성기 도움말](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="4cd76-129">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 [<span data-ttu-id="4cd76-130">식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4cd76-130">Expressions &#40;Report Builder and SSRS&#41;</span></span>](report-design/expressions-report-builder-and-ssrs.md)  
  
  
