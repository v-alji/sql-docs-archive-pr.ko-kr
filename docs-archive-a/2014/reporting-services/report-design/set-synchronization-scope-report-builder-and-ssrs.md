---
title: 동기화 범위 설정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6f4a11e6-6151-47be-a43f-e3dbf6c0e737
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3efbb7774d5116c9b3a18457291434f2a05aac7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639294"
---
# <a name="set-synchronization-scope-report-builder-and-ssrs"></a><span data-ttu-id="3ee09-102">동기화 범위 설정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3ee09-102">Set Synchronization Scope (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3ee09-103">표시기는 지정된 범위 내에서 전체 표시기 데이터 값 범위를 동기화하여 데이터 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3ee09-103">Indicators convey data values by synchronizing across the range of indicator values within a specified scope.</span></span> <span data-ttu-id="3ee09-104">이 범위는 기본적으로 표시기가 포함된 테이블, 행렬 등 표시기의 상위 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="3ee09-104">By default, the scope is the parent container of the indicator such as the table or matrix that contains the indicator.</span></span> <span data-ttu-id="3ee09-105">보고서 레이아웃에 따라 표시기 동기화를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ee09-105">You can change the synchronization of the indicator depending on the layout of your report.</span></span> <span data-ttu-id="3ee09-106">예를 들어 테이블 같은 데이터 영역에 행 그룹이 있는 경우 이 그룹을 표시기 범위로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ee09-106">For example, if a data region such as a table has a row group, you can specify the group as the indicator scope.</span></span> <span data-ttu-id="3ee09-107">표시기의 동기화를 생략할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ee09-107">The indicator can also omit synchronization.</span></span>  
  
 <span data-ttu-id="3ee09-108">식을 사용하여 단위 등의 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ee09-108">Options such as measurement units can be set by using expressions.</span></span> <span data-ttu-id="3ee09-109">자세한 내용은 [식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ee09-109">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="3ee09-110">보고서 내의 범위를 이해하고 설정하는 방법에 대한 일반적인 내용은 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ee09-110">For general information about understanding and setting scope within reports, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-synchronization-scope-of-an-indicator"></a><span data-ttu-id="3ee09-111">표시기의 동기화 범위를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="3ee09-111">To change the synchronization scope of an indicator</span></span>  
  
1.  <span data-ttu-id="3ee09-112">변경할 표시기를 마우스 오른쪽 단추로 클릭하고 **표시기 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee09-112">Right click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="3ee09-113">왼쪽 창에서 **값 및 상태** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee09-113">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="3ee09-114">**동기화 범위** 목록에서 적용할 범위를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee09-114">In the **Synchronization scope** list, click the scope that you want to apply.</span></span>  
  
     <span data-ttu-id="3ee09-115">**(없음)** 옵션(표시기에서 동기화 범위 제거)은 항상 사용할 수 있고</span><span class="sxs-lookup"><span data-stu-id="3ee09-115">The **(None)** option, which removes synchronization scope from the indicator, is always available.</span></span> <span data-ttu-id="3ee09-116">다른 옵션은 보고서 레이아웃에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3ee09-116">Other options depend on the layout of your report.</span></span>  
  
     <span data-ttu-id="3ee09-117">원하는 경우 **식** 단추(*fx*)를 클릭하여 범위를 설정하는 식을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="3ee09-117">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the scope.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3ee09-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ee09-118">See Also</span></span>  
 [<span data-ttu-id="3ee09-119">표시기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3ee09-119">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
