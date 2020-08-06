---
title: 보고서에 어셈블리 참조 추가(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom assemblies [Reporting Services], referencing
- custom code [Reporting Services]
- adding assembly references
- assemblies [Reporting Services], references
ms.assetid: 0a03939e-48ce-4c30-b227-98533f2e0ccb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23dda0c65589e55849f906c621e42ce70f0d7ab5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653214"
---
# <a name="add-an-assembly-reference-to-a-report-ssrs"></a><span data-ttu-id="a8c57-102">보고서에 어셈블리 참조 추가(SSRS)</span><span class="sxs-lookup"><span data-stu-id="a8c57-102">Add an Assembly Reference to a Report (SSRS)</span></span>
  <span data-ttu-id="a8c57-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 또는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]에 없는 <xref:System.Math> <xref:System.Convert> 클래스에 대한 참조가 포함된 사용자 지정 코드를 포함하는 경우 보고서 처리기가 이름을 확인할 수 있도록 보고서에 대한 어셈블리 참조를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c57-103">When you embed custom code that contains references to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes that are not in <xref:System.Math> or <xref:System.Convert>, you must provide an assembly reference to the report so that the report processor can resolve the names.</span></span> <span data-ttu-id="a8c57-104">자세한 내용은 [보고서에 코드 추가&#40;SSRS&#41;](add-code-to-a-report-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c57-104">For more information, see [Add Code to a Report &#40;SSRS&#41;](add-code-to-a-report-ssrs.md).</span></span>  
  
### <a name="to-add-an-assembly-reference-to-a-report"></a><span data-ttu-id="a8c57-105">보고서에 어셈블리 참조를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="a8c57-105">To add an assembly reference to a report</span></span>  
  
1.  <span data-ttu-id="a8c57-106">**디자인** 뷰에서 보고서 테두리 바깥쪽의 디자인 화면을 마우스 오른쪽 단추로 클릭하고 **보고서 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c57-106">In **Design** view, right-click the design surface outside the border of the report and click **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="a8c57-107">**참조**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c57-107">Click **References**.</span></span>  
  
3.  <span data-ttu-id="a8c57-108">**어셈블리 추가 또는 제거**에서 **추가** 를 클릭한 다음 줄임표 단추를 클릭하여 해당 어셈블리를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c57-108">In **Add or remove assemblies**, click **Add** and then click the ellipsis button to browse to the assembly.</span></span>  
  
4.  <span data-ttu-id="a8c57-109">**클래스 추가 또는 제거**에서 **추가** 를 클릭한 다음 클래스의 이름을 입력하고 보고서 내에서 사용할 인스턴스 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c57-109">In **Add or remove classes**, click **Add** and then type name of the class and provide an instance name to use within the report.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a8c57-110">인스턴스 기반 멤버에 대해서만 클래스 이름과 인스턴스 이름을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="a8c57-110">Specify a class and instance name only for instance-based members.</span></span> <span data-ttu-id="a8c57-111">**클래스** 목록에서 정적 멤버를 지정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="a8c57-111">Do not specify static members in the **Classes** list.</span></span> <span data-ttu-id="a8c57-112">자세한 내용은 [보고서 디자이너의 식에 포함된 사용자 지정 코드 및 어셈블리 참조&#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a8c57-112">For more information, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a8c57-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8c57-113">See Also</span></span>  
 <span data-ttu-id="a8c57-114">[보고서에서 사용자 지정 어셈블리 사용](../custom-assemblies/using-custom-assemblies-with-reports.md) </span><span class="sxs-lookup"><span data-stu-id="a8c57-114">[Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md) </span></span>  
 [<span data-ttu-id="a8c57-115">보고서 속성 대화 상자, 참조</span><span class="sxs-lookup"><span data-stu-id="a8c57-115">Report Properties Dialog Box, References</span></span>](../report-properties-dialog-box-references.md)  
  
  
