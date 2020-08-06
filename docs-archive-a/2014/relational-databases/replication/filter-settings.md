---
title: 필터 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d82d5f38eb460f392f1eb2ed3387ce3d97757db5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646895"
---
# <a name="filter-settings"></a><span data-ttu-id="58499-102">필터 설정</span><span class="sxs-lookup"><span data-stu-id="58499-102">Filter Settings</span></span>
  <span data-ttu-id="58499-103">**필터 설정** 대화 상자를 사용하여 복제 모니터에서 표에 사용할 필터를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58499-103">The **Filter Settings** dialog box lets you define filters for grids in Replication Monitor.</span></span> <span data-ttu-id="58499-104">예를 들어 **모든 구독** 탭에서 활성 상태인 구독만 표시하려면 **열 이름** 열에서 **상태** 를, **연산자** 열에서 **같음** 을, **값1** 열에서 **활성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58499-104">For example, to show only those subscriptions that are active on the **All Subscriptions** tab, select **Status** from the **Column Name** column, **Equals** from the **Operator** column, and **Active** from the **Value1** column.</span></span> <span data-ttu-id="58499-105">하나 이상의 열을 기준으로 필터를 정의하면 필터 조건과 일치하는 행만 표에 표시되도록 필터가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="58499-105">After you define a filter that is based one or more columns, the filter is applied so that the grid displays only the subset of rows that match the filter criteria.</span></span>  
  
## <a name="options"></a><span data-ttu-id="58499-106">옵션</span><span class="sxs-lookup"><span data-stu-id="58499-106">Options</span></span>  
 <span data-ttu-id="58499-107">**열 이름**</span><span class="sxs-lookup"><span data-stu-id="58499-107">**Column Name**</span></span>  
 <span data-ttu-id="58499-108">필터링할 열의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58499-108">Select the name of the column on which you want to filter.</span></span> <span data-ttu-id="58499-109">하나 이상의 열을 필터 기준으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58499-109">You can base a filter on one or more columns.</span></span>  
  
 <span data-ttu-id="58499-110">**연산자**</span><span class="sxs-lookup"><span data-stu-id="58499-110">**Operator**</span></span>  
 <span data-ttu-id="58499-111">**작거나 같음**등의 필터에 대한 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58499-111">Select an operator for the filter, such as **Less than or Equal to**.</span></span>  
  
 <span data-ttu-id="58499-112">**값1** 및 **값2**</span><span class="sxs-lookup"><span data-stu-id="58499-112">**Value1** and **Value2**</span></span>  
 <span data-ttu-id="58499-113">필터 값을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58499-113">Enter or select a value for the filter.</span></span> <span data-ttu-id="58499-114">대부분의 연산자는 **값1** 열에만 값을 입력하면 되지만 **사이** 및 **사이에 있지 않음** 연산자는 **값2** 열에도 값을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58499-114">Most operators only require a value in the **Value1** column, but the **Between** and **Not Between** operators also require a value in the **Value2** column.</span></span>  
  
 <span data-ttu-id="58499-115">**필터 지우기**</span><span class="sxs-lookup"><span data-stu-id="58499-115">**Clear Filter**</span></span>  
 <span data-ttu-id="58499-116">정의된 필터를 모두 지우려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58499-116">Click this button to clear all filters that have been defined.</span></span> <span data-ttu-id="58499-117">단일 필터를 제거하려면 필터 행을 선택하고 Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="58499-117">To remove a single filter, select the filter row and press the Delete key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58499-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58499-118">See Also</span></span>  
 [<span data-ttu-id="58499-119">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="58499-119">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
