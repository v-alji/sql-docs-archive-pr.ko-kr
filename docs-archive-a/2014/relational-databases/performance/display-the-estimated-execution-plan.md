---
title: 예상 실행 계획 표시 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- zoom [SQL Server]
- estimated execution plan [SQL Server]
- displaying execution plans
- viewing execution plans
- execution plans [SQL Server], displaying
- customizing execution plan display [SQL Server]
- modifying execution plan display
- custom zoom [SQL Server]
ms.assetid: e94aa576-4c0c-4c54-ad05-6c3432cc615b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79c0972661d40eb9e359cf43f7a1f0b1b2ae4b0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730532"
---
# <a name="display-the-estimated-execution-plan"></a><span data-ttu-id="04f7c-102">예상 실행 계획 표시</span><span class="sxs-lookup"><span data-stu-id="04f7c-102">Display the Estimated Execution Plan</span></span>
  <span data-ttu-id="04f7c-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 그래픽 예상 실행 계획을 작성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-103">This topic describes how to generate graphical estimated execution plans by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="04f7c-104">예상 실행 계획이 작성되면 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리 또는 일괄 처리가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-104">When estimated execution plans are generated, the [!INCLUDE[tsql](../../includes/tsql-md.md)] queries or batches do not execute.</span></span> <span data-ttu-id="04f7c-105">대신 쿼리가 실제로 실행되었을 때 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 이 사용할 가능성이 가장 큰 쿼리 실행 계획이 실행 계획을 통해 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-105">Instead, the execution plan that is generated displays the query execution plan that [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] would most probably use if the queries were actually executed.</span></span>  
  
 <span data-ttu-id="04f7c-106">이 기능을 사용하려면 사용자가 그래픽 실행 계획을 생성하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리를 실행하기 위한 적절한 권한을 갖고 있어야 하며 쿼리가 참조하는 모든 데이터베이스에 대한 SHOWPLAN 권한이 허용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-106">To use this feature, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../includes/tsql-md.md)] query for which a graphical execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.</span></span>  
  
### <a name="to-display-the-estimated-execution-plan-for-a-query"></a><span data-ttu-id="04f7c-107">쿼리의 예상 실행 계획을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="04f7c-107">To display the estimated execution plan for a query</span></span>  
  
1.  <span data-ttu-id="04f7c-108">도구 모음에서 **데이터베이스 엔진 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-108">On the toolbar, click **Database Engine Query**.</span></span> <span data-ttu-id="04f7c-109">**파일 열기** 도구 모음 단추를 클릭하여 기존 쿼리를 열고 예상 실행 계획을 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-109">You can also open an existing query and display the estimated execution plan by clicking the **Open File** toolbar button and locating the existing query.</span></span>  
  
2.  <span data-ttu-id="04f7c-110">예상 실행 계획을 표시할 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-110">Enter the query for which you would like to display the estimated execution plan.</span></span>  
  
3.  <span data-ttu-id="04f7c-111">**쿼리** 메뉴에서 **예상 실행 계획 표시** 를 클릭하거나 **예상 실행 계획 표시** 도구 모음 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-111">On the **Query** menu, click **Display Estimated Execution Plan** or click the **Display Estimated Execution Plan** toolbar button.</span></span> <span data-ttu-id="04f7c-112">예상 실행 계획은 결과 창의 **실행 계획** 탭에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-112">The estimated execution plan is displayed on the **Execution Plan** tab in the results pane.</span></span> <span data-ttu-id="04f7c-113">추가 정보를 보려면 논리 및 물리 연산자 아이콘 위에 마우스를 올리고 잠시 대기하여 도구 설명을 표시하고 연산자에 대한 설명 및 속성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-113">To view additional information, pause the mouse over the logical and physical operator icons and view the description and properties of the operator in the displayed ToolTip.</span></span> <span data-ttu-id="04f7c-114">또는 속성 창에서 연산자 속성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-114">Alternatively, you can view operator properties in the Properties window.</span></span> <span data-ttu-id="04f7c-115">속성이 보이지 않으면 연산자를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-115">If Properties is not visible, right-click an operator and click **Properties**.</span></span> <span data-ttu-id="04f7c-116">속성을 확인할 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-116">Select an operator to view its properties.</span></span>  
  
4.  <span data-ttu-id="04f7c-117">실행 계획 표시 크기를 변경하려면 실행 계획을 마우스 오른쪽 단추로 클릭한 다음 실행 계획, **축소**, **확대**, **사용자 지정 확대/축소**또는 **크기에 맞게**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-117">To alter the display of the execution plan, right-click the execution plan and select **Zoom In**, **Zoom Out**, **Custom Zoom**, or **Zoom to Fit**.</span></span> <span data-ttu-id="04f7c-118">**축소** 및 **확대** 를 사용하면 실행 계획을 고정된 크기만큼 확대 또는 축소시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-118">**Zoom In** and **Zoom Out** allow you to magnify or reduce the execution plan by fixed amounts.</span></span> <span data-ttu-id="04f7c-119">**사용자 지정 확대/축소** 를 사용하면 사용자가 원하는 표시 배율을 정의할 수 있습니다(예: 80%로 축소).</span><span class="sxs-lookup"><span data-stu-id="04f7c-119">**Custom Zoom** allows you to define your own display magnification, such as zooming at 80 percent.</span></span> <span data-ttu-id="04f7c-120">**크기에 맞게** 는 결과 창에 맞게 실행 계획을 확대합니다.</span><span class="sxs-lookup"><span data-stu-id="04f7c-120">**Zoom to Fit** magnifies the execution plan to fit the result pane.</span></span>  
  
  
