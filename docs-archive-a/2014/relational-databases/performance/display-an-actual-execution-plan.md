---
title: 실제 실행 계획 표시 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- displaying execution plans
- actual execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
ms.assetid: 9e583a18-5f4a-4054-bfe1-4b2a76630db6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f384e2d2752b7601fbb46b8ee7f7b56a2615651c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730544"
---
# <a name="display-an-actual-execution-plan"></a><span data-ttu-id="7b1e5-102">실제 실행 계획 표시</span><span class="sxs-lookup"><span data-stu-id="7b1e5-102">Display an Actual Execution Plan</span></span>
  <span data-ttu-id="7b1e5-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 실제 그래픽 실행 계획을 생성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-103">This topic describes how to generate actual graphical execution plans by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="7b1e5-104">실제 실행 계획을 생성하면 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리 또는 일괄 처리가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-104">When actual execution plans are generated, the [!INCLUDE[tsql](../../includes/tsql-md.md)] queries or batches execute.</span></span> <span data-ttu-id="7b1e5-105">생성된 실행 계획은 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 이 쿼리를 실행할 때 사용하는 실제 쿼리 실행 계획을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-105">The execution plan that is generated displays the actual query execution plan that the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses to execute the queries.</span></span>  
  
 <span data-ttu-id="7b1e5-106">이 기능을 사용하려면 사용자가 그래픽 실행 계획이 생성되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리를 실행할 적절한 권한을 가져야 하며 쿼리가 참조하는 모든 데이터베이스에 대해서도 SHOWPLAN 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-106">To use this feature, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../includes/tsql-md.md)] queries for which a graphical execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.</span></span>  
  
### <a name="to-include-an-execution-plan-for-a-query-during-execution"></a><span data-ttu-id="7b1e5-107">실행 중에 쿼리의 실행 계획을 포함하려면</span><span class="sxs-lookup"><span data-stu-id="7b1e5-107">To include an execution plan for a query during execution</span></span>  
  
1.  <span data-ttu-id="7b1e5-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 도구 모음에서 **데이터베이스 엔진 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-108">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] toolbar, click **Database Engine Query**.</span></span> <span data-ttu-id="7b1e5-109">**파일 열기** 도구 모음 단추를 클릭하여 기존 쿼리를 열고 예상 실행 계획을 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-109">You can also open an existing query and display the estimated execution plan by clicking the **Open File** toolbar button and locating the existing query.</span></span>  
  
2.  <span data-ttu-id="7b1e5-110">실제 실행 계획을 표시할 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-110">Enter the query for which you would like to display the actual execution plan.</span></span>  
  
3.  <span data-ttu-id="7b1e5-111">**쿼리** 메뉴에서 **실제 실행 계획 포함** 을 클릭 하거나 **실제 실행 계획 포함** 도구 모음 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-111">On the **Query** menu, click **Include Actual Execution Plan** or click the **Include Actual Execution Plan** toolbar button</span></span>  
  
4.  <span data-ttu-id="7b1e5-112">**실행** 도구 모음 단추를 클릭하여 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-112">Execute the query by clicking the **Execute** toolbar button.</span></span> <span data-ttu-id="7b1e5-113">쿼리 최적화 프로그램에서 사용하는 계획이 결과 창의 **실행 계획** 탭에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-113">The plan used by the query optimizer is displayed on the **Execution Plan** tab in the results pane.</span></span> <span data-ttu-id="7b1e5-114">표시된 도구 설명에서 연산자의 설명과 속성을 보려면 논리/물리 연산자 위에 마우스를 놓고 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-114">Pause the mouse over the logical and physical operators to view the description and properties of the operators in the displayed ToolTip.</span></span>  
  
     <span data-ttu-id="7b1e5-115">또는 속성 창에서 연산자 속성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-115">Alternatively, you can view operator properties in the Properties window.</span></span> <span data-ttu-id="7b1e5-116">속성이 표시되지 않으면 연산자를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-116">If Properties is not visible, right-click an operator and select **Properties**.</span></span> <span data-ttu-id="7b1e5-117">속성을 확인할 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-117">Select an operator to view its properties.</span></span>  
  
5.  <span data-ttu-id="7b1e5-118">실행 계획을 마우스 오른쪽 단추로 클릭하고 **확대**, **축소**, **사용자 지정 확대/축소**또는 **크기에 맞게**를 선택하여 실행 계획의 보기를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-118">You can alter the display of the execution plan by right-clicking the execution plan and selecting **Zoom In**, **Zoom Out**, **Custom Zoom**, or **Zoom to Fit**.</span></span> <span data-ttu-id="7b1e5-119">**확대** 및 **축소** 를 사용하면 실행 계획을 확대 또는 축소할 수 있으며 **사용자 지정 확대/축소** 를 사용하면 80% 축소와 같이 원하는 수준으로 확대 및 축소를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-119">**Zoom In** and **Zoom Out** allow you to zoom in or out on the execution plan, while **Custom Zoom** allows you to define your own zoom, such as zooming at 80 percent.</span></span> <span data-ttu-id="7b1e5-120">**크기에 맞게** 는 결과 창에 맞게 실행 계획을 확대합니다.</span><span class="sxs-lookup"><span data-stu-id="7b1e5-120">**Zoom to Fit** magnifies the execution plan to fit the result pane.</span></span>  
  
  
