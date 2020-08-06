---
title: '8단계: 1단원 패키지를 쉽게 이해할 수 있도록 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e3751e53-77c7-47d0-8fe8-73ed1a53413a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67fb8e2adb9062b5b777acc14df0ddc5b45884ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651121"
---
# <a name="step-8-making-the-lesson-1-package-easier-to-understand"></a><span data-ttu-id="805ca-102">8단계: 1단원 패키지를 쉽게 이해할 수 있도록 만들기</span><span class="sxs-lookup"><span data-stu-id="805ca-102">Step 8: Making the Lesson 1 Package Easier to Understand</span></span>
  <span data-ttu-id="805ca-103">1단원 패키지의 구성을 완료했으므로 이제 패키지 레이아웃을 정리하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-103">Now that you have completed the configuration of the Lesson 1 package, it is a good idea to tidy up the package layout.</span></span> <span data-ttu-id="805ca-104">제어 및 데이터 흐름 레이아웃 셰이프의 크기가 제멋대로이거나 셰이프가 정렬 또는 그룹화되지 않은 경우 패키지의 기능을 이해하기가 매우 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-104">If the shapes in the control and data flow layouts are random sizes, or if the shapes are not aligned or grouped, the functionality of package can be more difficult to understand.</span></span>  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="805ca-105">Data Tools에서는 패키지 레이아웃의 서식을 쉽고 빠르게 지정할 수 있는 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-105">Data Tools provides tools that make it easy and quick to format the package layout.</span></span> <span data-ttu-id="805ca-106">서식 지정 기능에는 셰이프의 크기를 동일하게 지정하고 셰이프를 정렬하며 셰이프 간의 가로 및 세로 간격을 조정하는 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-106">The formatting features include the ability to make shapes the same size, align shapes, and manipulate the horizontal and vertical spacing between shapes.</span></span>  
  
 <span data-ttu-id="805ca-107">패키지 기능에 대한 이해를 향상시킬 수 있는 다른 방법은 패키지 기능을 설명하는 주석을 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-107">Another way to improve the understanding of package functionality is to add annotations that describe package functionality.</span></span>  
  
 <span data-ttu-id="805ca-108">이 태스크에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools의 서식 지정 기능을 사용하여 데이터 흐름의 레이아웃을 개선하고 데이터 흐름에 주석도 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-108">In this task, you will use the formatting features in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools to improve the layout of the data flow and also add an annotation to the data flow.</span></span>  
  
### <a name="to-format-the-layout-of-the-data-flow"></a><span data-ttu-id="805ca-109">데이터 흐름 레이아웃의 서식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="805ca-109">To format the layout of the data flow</span></span>  
  
1.  <span data-ttu-id="805ca-110">1단원 패키지를 아직 열지 않은 경우 솔루션 탐색기에서 Lesson 1.dtsx를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-110">If the Lesson 1 package is not already open, double-click Lesson 1.dtsx in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="805ca-111">**데이터 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-111">Click the **Data Flow** tab.</span></span>  
  
3.  <span data-ttu-id="805ca-112">Extract Sample Currency 변환의 오른쪽 위에 커서를 놓고 클릭한 다음 데이터 흐름 구성 요소 전체를 포함하도록 커서를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-112">Place the cursor to the top and to the right of the Extract Sample Currency transformation, click, and then drag the cursor across all the data flow components.</span></span>  
  
4.  <span data-ttu-id="805ca-113">**서식** 메뉴에서 **같은 크기로**를 가리킨 다음 **모두**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-113">On the **Format** menu, point to **Make Same Size**, and then click **Both**.</span></span>  
  
5.  <span data-ttu-id="805ca-114">데이터 흐름 개체를 선택한 경우에는 **서식** 메뉴에서 **맞춤**을 가리킨 다음 **왼쪽**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-114">With the data flow objects selected, on the **Format** menu, point to **Align**, and then click **Lefts**.</span></span>  
  
### <a name="to-add-an-annotation-to-the-data-flow"></a><span data-ttu-id="805ca-115">데이터 흐름에 주석을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="805ca-115">To add an annotation to the data flow</span></span>  
  
1.  <span data-ttu-id="805ca-116">데이터 흐름 디자인 화면 배경의 아무 위치나 마우스 오른쪽 단추로 클릭한 다음 **주석 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-116">Right-click anywhere in the background of the data flow design surface and then click **Add Annotation**.</span></span>  
  
2.  <span data-ttu-id="805ca-117">주석 상자에 다음 텍스트를 입력하거나 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-117">Type or paste the following text in the annotation box.</span></span>  
  
     <span data-ttu-id="805ca-118">**데이터 흐름이 파일에서 데이터를 추출하고 DimCurrency 테이블의 CurrencyKey 열과 DimDate 테이블의 DateKey 열에서 값을 조회한 다음 NewFactCurrencyRate 테이블에 데이터를 기록합니다.**</span><span class="sxs-lookup"><span data-stu-id="805ca-118">**The data flow extracts data from a file, looks up values in the CurrencyKey column in the DimCurrency table and the DateKey column in the DimDate table, and writes the data to the NewFactCurrencyRate table.**</span></span>  
  
     <span data-ttu-id="805ca-119">주석 상자에서 텍스트 줄을 바꾸려면 새로운 줄을 시작할 위치에 커서를 놓고 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-119">To wrap the text in the annotation box, place the cursor where you want to start a new line and press the Enter key.</span></span>  
  
     <span data-ttu-id="805ca-120">주석 상자에 텍스트를 추가하지 않은 경우 상자의 바깥쪽을 클릭하면 주석 상자가 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="805ca-120">If you do not add text to the annotation box, it disappears when you click outside the box.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="805ca-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="805ca-121">Next Steps</span></span>  
 [<span data-ttu-id="805ca-122">9단계: 1단원 자습서 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="805ca-122">Step 9: Testing the Lesson 1 Tutorial Package</span></span>](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
  
