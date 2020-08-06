---
title: 데이터 탐색 (데이터 마이닝 추가 기능 SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- histogram [data mining]
- data visualization
ms.assetid: 714845a9-4c27-461a-9ba3-149e1e818386
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2572c11e92dcf99dfa3adf661603e8f65f05116e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734559"
---
# <a name="explore-data-sql-server-data-mining-add-ins"></a><span data-ttu-id="2fa5a-102">데이터 탐색(SQL Server 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="2fa5a-102">Explore Data (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="2fa5a-103">![데이터 탐색 마법사](media/dmc-explore.gif "데이터 탐색 마법사")</span><span class="sxs-lookup"><span data-stu-id="2fa5a-103">![Explore Data wizard](media/dmc-explore.gif "Explore Data wizard")</span></span>  
  
 <span data-ttu-id="2fa5a-104">**데이터 탐색** 마법사를 사용 하 여 데이터 테이블에 있는 데이터의 유형과 크기를 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-104">The **Explore Data** wizard helps you understand the type and amount of data in your data table.</span></span> <span data-ttu-id="2fa5a-105">이 마법사는 선택한 열에 대한 분포와 값을 한 번에 한 열씩 그래프로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-105">The wizard graphs the distribution and values for the selected columns, one column at a time.</span></span> <span data-ttu-id="2fa5a-106">그러면 데이터 그룹화 방식을 변경하여 시험해 보거나 내용을 표시하는 차트를 Excel 통합 문서에 복사하여 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-106">You can then experiment with changing the way that data is grouped, or copy the chart that shows the content to an Excel workbook for review.</span></span>  
  
 <span data-ttu-id="2fa5a-107">데이터에 연속 숫자 데이터가 포함된 경우 다음 두 뷰 사이를 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-107">If your data contains continuous numeric data, you can toggle between these two views:</span></span>  
  
-   <span data-ttu-id="2fa5a-108">**선 그래프입니다.**</span><span class="sxs-lookup"><span data-stu-id="2fa5a-108">**Line graph.**</span></span> <span data-ttu-id="2fa5a-109">이 그래프는 X축에는 데이터 값이 Y축에는 사례 수가 있는 그래프입니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-109">This graph charts the data values on the X-axis and the number of cases on the y-axis.</span></span>  
  
-   <span data-ttu-id="2fa5a-110">**가로 막대형 차트입니다.**</span><span class="sxs-lookup"><span data-stu-id="2fa5a-110">**Bar chart.**</span></span> <span data-ttu-id="2fa5a-111">이 그래프는 각 값에 대한 사례 수로 값을 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-111">This graph groups values by the number of cases for each value.</span></span>  
  
 <span data-ttu-id="2fa5a-112">마법사가 데이터에서 그룹을 찾으면 데이터 값의 실제 분포가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-112">When the wizard finds groups in the data, it uses the actual distribution of data values.</span></span> <span data-ttu-id="2fa5a-113">따라서 가로 막대형 차트는 10 또는 100과 같은 일반적인 정수 숫자 축 표식을 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-113">Therefore, the bar chart does not show typical whole-number numeric axis markers such as 10 or 100.</span></span> <span data-ttu-id="2fa5a-114">대신 가로 막대형 차트에 표시되는 범위는 43521-55603(Income 열의 경우)과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-114">Instead, the ranges shown in the bar chart might be something like 43521-55603 (for the Income column).</span></span>  
  
 <span data-ttu-id="2fa5a-115">다른 범위로 데이터를 그룹화하려면 데이터를 분석하기 전에 Excel에서 이 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-115">If you want to group your data into other ranges, you should do this in Excel before analyzing the data.</span></span> <span data-ttu-id="2fa5a-116">또는 [레이블 재지정](relabel-sql-server-data-mining-add-ins.md) 마법사를 사용 하 여 데이터를 레이블 재지정 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-116">Or, you can relabel the data by using the [Relabel](relabel-sql-server-data-mining-add-ins.md) wizard.</span></span>  
  
## <a name="using-the-explore-data-wizard"></a><span data-ttu-id="2fa5a-117">데이터 탐색 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="2fa5a-117">Using the Explore Data Wizard</span></span>  
  
1.  <span data-ttu-id="2fa5a-118">**데이터 마이닝** 리본에서 **데이터 탐색**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-118">In the **Data Mining** ribbon, click **Explore Data**.</span></span>  
  
2.  <span data-ttu-id="2fa5a-119">**원본 선택** 대화 상자에서 데이터를 포함 하는 테이블 또는 셀 범위를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-119">In the **Select Source** dialog box, select the table or range of cells that contains your data.</span></span>  
  
3.  <span data-ttu-id="2fa5a-120">**열 선택** 대화 상자에서 분석할 열을 창에 표시 된 샘플 데이터에서 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-120">In the **Select Column** dialog box, choose the column to analyze, from the sample data displayed in the pane.</span></span>  
  
4.  <span data-ttu-id="2fa5a-121">**데이터 탐색** 대화 상자에서 데이터 분포를 표시할 차트 종류를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-121">In the **Explore Data** dialog box, choose the chart types for displaying the distribution of data.</span></span>  
  
5.  <span data-ttu-id="2fa5a-122">필요에 따라 새 열을 데이터에 추가하거나 데이터 분할 방식을 변경하거나 차트를 Excel로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-122">Optionally, you can add new columns to the data, change the way that the data is segmented, or copy the chart to Excel.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="2fa5a-123">요구 사항</span><span class="sxs-lookup"><span data-stu-id="2fa5a-123">Requirements</span></span>  
 <span data-ttu-id="2fa5a-124">**데이터 탐색** 마법사를 사용 하려면 데이터가 Excel 데이터 테이블에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fa5a-124">To use the **Explore Data** wizard, your data must be in an Excel data table.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="2fa5a-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2fa5a-125">See Also</span></span>  
 [<span data-ttu-id="2fa5a-126">데이터 마이닝 준비 검사 목록</span><span class="sxs-lookup"><span data-stu-id="2fa5a-126">Checklist of Preparation for Data Mining</span></span>](checklist-of-preparation-for-data-mining.md)  
  
  
