---
title: 보고서에 코드 추가(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- code [Reporting Services]
- custom code [Reporting Services]
- expressions [Reporting Services], code
- adding code
- reports [Reporting Services], code
ms.assetid: 00ef8fc6-99fe-49b2-8a22-7eb475881dc4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c1964e69d00e1a27da29ce8cfb73b7bee1bece7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733655"
---
# <a name="add-code-to-a-report-ssrs"></a><span data-ttu-id="fb836-102">보고서에 코드 추가(SSRS)</span><span class="sxs-lookup"><span data-stu-id="fb836-102">Add Code to a Report (SSRS)</span></span>
  <span data-ttu-id="fb836-103">모든 식에서 고유한 사용자 지정 코드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb836-103">In any expression, you can call your own custom code.</span></span> <span data-ttu-id="fb836-104">다음과 같은 두 가지 방법으로 코드를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb836-104">You can provide code in the following two ways:</span></span>  
  
-   <span data-ttu-id="fb836-105">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 으로 작성된 코드를 보고서에 직접 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fb836-105">Embed code written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] directly in your report.</span></span> <span data-ttu-id="fb836-106">코드가 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 또는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]가 아닌 <xref:System.Math> <xref:System.Convert>를 참조하는 경우 보고서에 해당 참조를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb836-106">If your code refers to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] that is not <xref:System.Math> or <xref:System.Convert>, you must add the reference to the report.</span></span> <span data-ttu-id="fb836-107">자세한 내용은 [보고서에 어셈블리 참조 추가&#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb836-107">For more information, see [Add an Assembly Reference to a Report &#40;SSRS&#41;](add-an-assembly-reference-to-a-report-ssrs.md).</span></span> <span data-ttu-id="fb836-108">코드에서 만들 수 있는 기타 참조에 대한 자세한 내용은 [보고서 디자이너의 식에 포함된 사용자 지정 코드 및 어셈블리 참조&#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb836-108">For more information about other references you can make from your code, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
-   <span data-ttu-id="fb836-109">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]를 사용하여 사용자 지정 코드 어셈블리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fb836-109">Provide a custom code assembly by using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="fb836-110">사용자 지정 어셈블리를 제공하는 경우 보고서를 작성하는 컴퓨터와 보고서를 보는 보고서 서버 모두에 해당 어셈블리를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb836-110">If you provide a custom assembly, you must install it on both the computer where you author the report and the report server where you view the report.</span></span> <span data-ttu-id="fb836-111">자세한 내용은 [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb836-111">For more information, see [Using Custom Assemblies with Reports](../custom-assemblies/using-custom-assemblies-with-reports.md).</span></span>  
  
### <a name="to-add-embedded-code-to-a-report"></a><span data-ttu-id="fb836-112">보고서에 포함 코드를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="fb836-112">To add embedded code to a report</span></span>  
  
1.  <span data-ttu-id="fb836-113">**디자인** 뷰에서 보고서 테두리 바깥쪽의 디자인 화면을 마우스 오른쪽 단추로 클릭하고 **보고서 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb836-113">In **Design** view, right-click the design surface outside the border of the report and click **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="fb836-114">**코드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fb836-114">Click **Code**.</span></span>  
  
3.  <span data-ttu-id="fb836-115">**사용자 지정 코드**에 코드를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fb836-115">In **Custom code**, type the code.</span></span> <span data-ttu-id="fb836-116">코드에 오류가 있으면 보고서 실행 시 경고가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="fb836-116">Errors in the code produce warnings when the report runs.</span></span> <span data-ttu-id="fb836-117">다음 예에서는 " `ChangeWord` "라는 단어를 "`Bike`"로 바꾸는`Bicycle`라는 사용자 지정 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fb836-117">The following example creates a custom function named `ChangeWord` that replaces the word "`Bike`" with "`Bicycle`".</span></span>  
  
    ```  
    Public Function ChangeWord(ByVal s As String) As String  
       Dim strBuilder As New System.Text.StringBuilder(s)  
       If s.Contains("Bike") Then  
          strBuilder.Replace("Bike", "Bicycle")  
          Return strBuilder.ToString()  
          Else : Return s  
       End If  
    End Function  
    ```  
  
4.  <span data-ttu-id="fb836-118">다음 예에서는 하나의 식을 사용하여 Category라는 데이터 세트 필드를 이 함수에 전달하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fb836-118">The following example shows how to pass a dataset field named Category to this function in an expression:</span></span>  
  
    ```  
    =Code.ChangeWord(Fields!Category.Value)  
    ```  
  
     <span data-ttu-id="fb836-119">범주 값을 표시하는 테이블 셀에 이 식을 추가하면 해당 행의 데이터 세트 필드에 "Bike"라는 단어가 있을 때마다 해당 테이블 셀 값이 "Bicycle"이라는 단어를 대신 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fb836-119">If you add this expression to a table cell that displays category values, whenever the word "Bike" is in the dataset field for that row, the table cell value displays the word "Bicycle" instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb836-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb836-120">See Also</span></span>  
 <span data-ttu-id="fb836-121">[보고서 속성 대화 상자, 코드](../report-properties-dialog-box-code.md) </span><span class="sxs-lookup"><span data-stu-id="fb836-121">[Report Properties Dialog Box, Code](../report-properties-dialog-box-code.md) </span></span>  
 <span data-ttu-id="fb836-122">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fb836-122">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="fb836-123">매개 변수 컬렉션 참조&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="fb836-123">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
