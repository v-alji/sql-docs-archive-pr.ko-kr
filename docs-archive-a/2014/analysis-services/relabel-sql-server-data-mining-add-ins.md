---
title: 레이블 재지정 (SQL Server 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- relabel
- data cleaning
ms.assetid: af041b39-fdd1-4cb5-a5ef-2f3ddab84614
author: minewiskan
ms.author: owend
ms.openlocfilehash: a625676f60e2da32e19b85a94002b51eeb9ac816
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651287"
---
# <a name="relabel-sql-server-data-mining-add-ins"></a><span data-ttu-id="110e7-102">레이블 재지정(SQL Server 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="110e7-102">Relabel (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="110e7-103">![레이블 재지정 도구에 대한 Office 13 아이콘](media/dm13-relabel.gif "레이블 재지정 도구에 대한 Office 13 아이콘")</span><span class="sxs-lookup"><span data-stu-id="110e7-103">![Office 13 icon for Relabel tool](media/dm13-relabel.gif "Office 13 icon for Relabel tool")</span></span>

 <span data-ttu-id="110e7-104">Excel용 데이터 마이닝 클라이언트를 사용하면 분석 결과를 보다 쉽게 이해할 수 있도록 새 데이터 레이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-104">The Data Mining Client for Excel helps you create new labels for data to make it easier to understand the results of analysis.</span></span>

 <span data-ttu-id="110e7-105">레이블 재지정 이유는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-105">Reasons for relabeling include:</span></span>

-   <span data-ttu-id="110e7-106">데이터에 코딩된 결과(예: 남자의 경우 1, 여자의 경우 2)가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-106">The data includes results that were coded, such as 1 for Male and 2 for Female.</span></span>

-   <span data-ttu-id="110e7-107">숫자 값을 버킷팅하고 있고 범위에 설명이 포함된 이름을 지정하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-107">You are bucketing numeric values and want to give the ranges a descriptive name.</span></span>

-   <span data-ttu-id="110e7-108">긴 이름을 단순화하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-108">You want to simplify long names.</span></span>

## <a name="using-the-relabel-wizard"></a><span data-ttu-id="110e7-109">레이블 재지정 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="110e7-109">Using the Relabel Wizard</span></span>

1.  <span data-ttu-id="110e7-110">**데이터 마이닝** 리본에서 **정리** 를 클릭한 다음 **레이블 재지정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-110">In the **Data Mining** ribbon, click **Clean** and then select **Re-Label**.</span></span>

2.  <span data-ttu-id="110e7-111">수정하려는 데이터가 포함된 테이블 또는 데이터 범위를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-111">Select the table or data range that has the data you want to fix.</span></span>

3.  <span data-ttu-id="110e7-112">마법사의 **레이블 재지정** 페이지에서 드롭다운 목록의 열을 선택하거나 **데이터 샘플** 창의 열을 클릭하여 단일 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-112">In the **Re-label** page of the wizard, select a single column, either by choosing the column from the dropdown list, or by clicking the column in the **Data samples** pane.</span></span>

     <span data-ttu-id="110e7-113">**데이터 샘플** 창은 약 50개의 데이터 행만 표시하지만 이들은 값의 좋은 분포를 확인할 수 있도록 샘플링됩니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-113">The **Data samples** pane only shows about 50 rows of data, but they are sampled to ensure that you see a good spread of values.</span></span>

     <span data-ttu-id="110e7-114">**개수** 의 개수 헤더를 클릭하여 각 값의 개수를 기준으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-114">Click the column header for **Count** to sort by the count of each value.</span></span>

     <span data-ttu-id="110e7-115">**원래 레이블**로 정렬할 수도 있습니다. 이것은 가장 높거나 낮은 값을 먼저 다시 레이블 지정하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-115">You can also sort by **Original Labels**, which is handy if you want to re-label all the highest or lowest values first.</span></span>

4.  <span data-ttu-id="110e7-116">마법사의 **레이블 재지정** 데이터 페이지에서 **원래 레이블** 열의 값을 검토하여 이러한 값을 어떻게 그룹화하거나 편집할지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-116">In the **Re-label** data page of the wizard, review the values in the **Original Labels** column, and decide how you want to group or edit them.</span></span>

5.  <span data-ttu-id="110e7-117">**새로운 레이블**아래의 행에 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-117">Type a new value into the row under **New Labels**.</span></span> <span data-ttu-id="110e7-118">기존 값 목록에서 값을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-118">You can also choose a value from the list of existing values.</span></span> <span data-ttu-id="110e7-119">새 값을 입력하면 즉시 다시 사용 가능하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-119">As you type new values, they become available for re-use right away.</span></span>

6.  <span data-ttu-id="110e7-120">충분 한 행을 입력 한 후 **다음**을 클릭 하 고 **대상 선택** 페이지에서 레이블 재지정 데이터를 저장할 위치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-120">When you have entered enough rows, click **Next**, and on the **Select Destination** page, choose where you'll save the relabeled data.</span></span>

    -   <span data-ttu-id="110e7-121">**현재 워크시트에 새 열로 추가**</span><span class="sxs-lookup"><span data-stu-id="110e7-121">**Add as a new column to the current worksheet**</span></span>

         <span data-ttu-id="110e7-122">새 값을 포함하는 테이블에 새 열을 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-122">Click to add a new column to the table that contains the new values.</span></span>

    -   <span data-ttu-id="110e7-123">**시트 데이터와 해당 변경 내용을 새 워크시트에 복사**</span><span class="sxs-lookup"><span data-stu-id="110e7-123">**Copy sheet data with changes to a new worksheet**</span></span>

         <span data-ttu-id="110e7-124">업데이트된 데이터를 포함하는 새 워크시트를 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-124">Click to create a new worksheet that contains the updated data.</span></span>

    -   <span data-ttu-id="110e7-125">**현재 위치에서 데이터 변경**</span><span class="sxs-lookup"><span data-stu-id="110e7-125">**Change data in place**</span></span>

         <span data-ttu-id="110e7-126">원래 데이터를 새 값으로 바꾸려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="110e7-126">Click to replace the original data with the new values.</span></span>

## <a name="see-also"></a><span data-ttu-id="110e7-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="110e7-127">See Also</span></span>
 [<span data-ttu-id="110e7-128">데이터 탐색 및 지우기</span><span class="sxs-lookup"><span data-stu-id="110e7-128">Exploring and Cleaning Data</span></span>](exploring-and-cleaning-data.md)


