---
title: Excel 행 제한 해결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a4c8700b-bef5-4440-a99c-bba5dcc46bfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 128f65cf09833d23234da10bf7744c6ce30065ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648309"
---
# <a name="work-around-the-excel-row-limitation"></a><span data-ttu-id="3e3a0-102">Excel 행 제한 해결</span><span class="sxs-lookup"><span data-stu-id="3e3a0-102">Work Around the Excel Row Limitation</span></span>
  <span data-ttu-id="3e3a0-103">이 항목에서는 보고서를 Excel로 내보낼 때 Excel 2003 행 제한을 해결하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-103">This topic explains how to work around the Excel 2003 row limitation when you export reports to Excel.</span></span> <span data-ttu-id="3e3a0-104">테이블만 포함하는 보고서에 대한 해결 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-104">The workaround is for a report that contains only a table.</span></span>  
  
 <span data-ttu-id="3e3a0-105">Excel 2003은 워크시트당 최대 65,536개 행을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-105">Excel 2003 supports a maximum of 65,536 rows per worksheet.</span></span> <span data-ttu-id="3e3a0-106">특정 행 수 이후 명시적 페이지 나누기를 강제로 수행하여 이 제한을 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-106">You can work around this limitation by forcing an explicit page break after a certain number of rows.</span></span> <span data-ttu-id="3e3a0-107">Excel 렌더러는 각 명시적 페이지 나누기에 대해 새 워크시트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-107">The Excel renderer creates a new worksheet for each explicit page break.</span></span>  
  
### <a name="to-create-an-explicit-page-break"></a><span data-ttu-id="3e3a0-108">명시적 페이지 나누기를 만들려면</span><span class="sxs-lookup"><span data-stu-id="3e3a0-108">To create an explicit page break</span></span>  
  
1.  <span data-ttu-id="3e3a0-109">[!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] 또는 보고서 관리자에서 보고서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-109">Open the report in [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] or Report Manager.</span></span>  
  
2.  <span data-ttu-id="3e3a0-110">테이블에서 데이터 행을 마우스 오른쪽 단추로 클릭 한 다음 **그룹 추가**  >  **상위 그룹** 을 클릭 하 여 외부 테이블 그룹을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-110">Right click the Data row in the table, and then click **Add Group** > **Parent Group** to add an outer table group.</span></span>  
  
     <span data-ttu-id="3e3a0-111">![부모 그룹 선택](../media/datarow-selectparentgroup.png "부모 그룹 선택")</span><span class="sxs-lookup"><span data-stu-id="3e3a0-111">![Select the Parent Group](../media/datarow-selectparentgroup.png "Select the Parent Group")</span></span>  
  
3.  <span data-ttu-id="3e3a0-112">**그룹화 방법** 식 상자에 다음 수식을 입력한 다음 **확인** 을 클릭하여 상위 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-112">Enter the following formula in the **Group by** expression box, and then click **OK** to add the parent group.</span></span>  
  
     <span data-ttu-id="3e3a0-113">=Int((RowNumber(Nothing)-1)/65000)</span><span class="sxs-lookup"><span data-stu-id="3e3a0-113">=Int((RowNumber(Nothing)-1)/65000)</span></span>  
  
     <span data-ttu-id="3e3a0-114">수식은 숫자를 데이터 세트의 65000개 행 집합 각각에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-114">The formula assigns a number to each set of 65000 rows in the dataset.</span></span> <span data-ttu-id="3e3a0-115">그룹에 페이지 나누기가 정의되어 있는 경우 식을 사용하면 65000개 행마다 페이지가 나눠집니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-115">When a page break is defined for the group, the expression results in a page break every 65000 rows.</span></span>  
  
     <span data-ttu-id="3e3a0-116">외부 테이블 그룹을 추가하면 그룹 열이 보고서에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-116">Adding the outer table group adds a group column to the report.</span></span>  
  
4.  <span data-ttu-id="3e3a0-117">열 머리글을 마우스 오른쪽 단추로 클릭하고 **열 삭제**를 클릭한 다음 **열만 삭제**를 선택하여 그룹 열을 삭제하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-117">Delete the group column by right-clicking on the column header, clicking **Delete Columns**, selecting **Delete columns only**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="3e3a0-118">![그룹 열 삭제](../media/groupcolumn-delete-updated.png "그룹 열 삭제")</span><span class="sxs-lookup"><span data-stu-id="3e3a0-118">![Delete a group column](../media/groupcolumn-delete-updated.png "Delete a group column")</span></span>  
  
5.  <span data-ttu-id="3e3a0-119">**행 그룹** 섹션에서 **그룹 1** 을 마우스 오른쪽 단추로 클릭한 다음 **그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-119">Right click **Group 1** in the **Row Groups** section, and then click **Group Properties**.</span></span>  
  
     <span data-ttu-id="3e3a0-120">![그룹 속성 보기](../media/groupproperties-updated.png "그룹 속성 보기")</span><span class="sxs-lookup"><span data-stu-id="3e3a0-120">![View group properties](../media/groupproperties-updated.png "View group properties")</span></span>  
  
6.  <span data-ttu-id="3e3a0-121">**그룹 속성** 대화 상자의 **정렬** 페이지에서 기본 정렬 옵션을 선택하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-121">On the **Sorting** page of the **Group Properties** dialog box, select the default sorting option and click **Delete**.</span></span>  
  
     <span data-ttu-id="3e3a0-122">![기본 정렬 삭제](../media/groupproperties-sorting-updated.png "기본 정렬 삭제")</span><span class="sxs-lookup"><span data-stu-id="3e3a0-122">![Delete default sorting](../media/groupproperties-sorting-updated.png "Delete default sorting")</span></span>  
  
7.  <span data-ttu-id="3e3a0-123">**페이지 나누기** 페이지에서 **각 그룹 인스턴스 사이** 를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-123">On the **Page Breaks** page, click **Between each instance of a group** and then click **OK**.</span></span>  
  
     <span data-ttu-id="3e3a0-124">![페이지 나누기 설정](../media/groupproperties-pagebreaks-updated.png "페이지 나누기 설정")</span><span class="sxs-lookup"><span data-stu-id="3e3a0-124">![Set page breaks](../media/groupproperties-pagebreaks-updated.png "Set page breaks")</span></span>  
  
8.  <span data-ttu-id="3e3a0-125">보고서를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-125">Save the report.</span></span> <span data-ttu-id="3e3a0-126">보고서를 Excel로 내보내는 경우 여러 워크시트로 내보내고 각 워크시트에는 최대 65000개 행이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e3a0-126">When you export it to Excel, it exports to multiple worksheets and each worksheet contains a maximum of 65000 rows.</span></span>  
  
  
