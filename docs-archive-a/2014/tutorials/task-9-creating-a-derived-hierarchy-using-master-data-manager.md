---
title: '태스크 9: 마스터 데이터 관리자을 사용 하 여 파생 계층 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3bd2ec05-933f-4947-b1fe-c9226961eb7d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 5c85750e4556722c6e6a5edbccb4a3c82c119a74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742679"
---
# <a name="task-9-creating-a-derived-hierarchy-using-master-data-manager"></a><span data-ttu-id="ff2b5-102">태스크 9: 마스터 데이터 관리자를 사용하여 파생 계층 만들기</span><span class="sxs-lookup"><span data-stu-id="ff2b5-102">Task 9: Creating a Derived Hierarchy using Master Data Manager</span></span>
  <span data-ttu-id="ff2b5-103">이 작업에서는 마스터 데이터 관리자를 사용하여 파생 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-103">In this task, you create a derived hierarchy by using Master Data Manager.</span></span> <span data-ttu-id="ff2b5-104">이 파생 계층은 **공급자** 와 **상태** 엔터티 간의 도메인 기반 특성 관계에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-104">This derived hierarchy is derived from the domain-based attribute relationships between the **Supplier** and **State** entities.</span></span>  
  
1.  <span data-ttu-id="ff2b5-105">페이지 맨 위에 있는 **SQL Server 2012 MDS(Master Data Services)** 를 클릭 하 여 **마스터 데이터 관리자** 의 기본 페이지로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-105">Switch to the main page of **Master Data Manager** by clicking **SQL Server 2012 Master Data Services** at the top of the page.</span></span>  
  
2.  <span data-ttu-id="ff2b5-106">**관리 작업** 섹션에서 **시스템 관리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-106">Click **System Administration** in the **Administrative Tasks** section.</span></span>  
  
3.  <span data-ttu-id="ff2b5-107">메뉴 모음에서 **관리** 위로 마우스를 가져가서 **파생 계층**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-107">Hover the mouse over **Manage** on the menu bar, and click **Derived Hierarchies**.</span></span>  
  
     <span data-ttu-id="ff2b5-108">![관리 메뉴 - 선택한 파생 계층](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "관리 메뉴 - 선택한 파생 계층")</span><span class="sxs-lookup"><span data-stu-id="ff2b5-108">![Manage Menu - Derived Hierarchies Selected](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-01.jpg "Manage Menu - Derived Hierarchies Selected")</span></span>  
  
4.  <span data-ttu-id="ff2b5-109">도구 모음에서 **파생 계층 추가 (+)** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-109">Click **Add Derived Hierarchy (+)** button on the toolbar.</span></span>  
  
     <span data-ttu-id="ff2b5-110">![파생 계층 추가 단추](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "파생 계층 추가 단추")</span><span class="sxs-lookup"><span data-stu-id="ff2b5-110">![Add Derived Hierarchy Button](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-02.jpg "Add Derived Hierarchy Button")</span></span>  
  
5.  <span data-ttu-id="ff2b5-111">**파생 계층 이름**에 **SuppliersInState** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-111">Type **SuppliersInState** for the **Derived hierarchy name**.</span></span>  
  
6.  <span data-ttu-id="ff2b5-112">도구 모음에서 **저장** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-112">Click **Save** button on the toolbar.</span></span>  
  
     <span data-ttu-id="ff2b5-113">![파생 계층 저장 단추](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "파생 계층 저장 단추")</span><span class="sxs-lookup"><span data-stu-id="ff2b5-113">![Save Derived Hierarchy Button](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-03.jpg "Save Derived Hierarchy Button")</span></span>  
  
7.  <span data-ttu-id="ff2b5-114">**공급 업체** 를 **사용 가능한 수준: SuppliersInState** 에서 **현재 수준: SuppliersInState**로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-114">Drag **Supplier** from **Available Levels: SuppliersInState** to **Current Levels: SuppliersInState**.</span></span>  
  
     <span data-ttu-id="ff2b5-115">![현재 수준에 사용 가능한 엔터티 및 계층](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "현재 수준에 사용 가능한 엔터티 및 계층")</span><span class="sxs-lookup"><span data-stu-id="ff2b5-115">![Avialble Entities and Hierarchies to Current Level](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-04.jpg "Avialble Entities and Hierarchies to Current Level")</span></span>  
  
8.  <span data-ttu-id="ff2b5-116">**사용 가능한 수준: SuppliersInState** 에서 **현재 수준: SuppliersInState**로 **상태** 를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-116">Drag **State** from **Available Levels: SuppliersInState** to **Current Levels: SuppliersInState**.</span></span> <span data-ttu-id="ff2b5-117">화면에는 다음 그림과 같이 **현재 수준이** 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-117">The screen should have **Current Levels** as shown in the following picture.</span></span>  
  
     <span data-ttu-id="ff2b5-118">![현재 수준 및 파생 계층의 미리 보기](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "현재 수준 및 파생 계층의 미리 보기")</span><span class="sxs-lookup"><span data-stu-id="ff2b5-118">![Current Levels and Preview of Derived Hierarchy](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-05.jpg "Current Levels and Preview of Derived Hierarchy")</span></span>  
  
9. <span data-ttu-id="ff2b5-119">**미리 보기** 창에서 사용자 **{뉴욕}** 을 (를) 확장 하면 이전 이미지에 표시 된 것 처럼 해당 상태에서 하나의 공급자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-119">In the **Preview** window, expand **NY { New York}** and you should see one supplier in that state as shown in the preceding image.</span></span>  
  
10. <span data-ttu-id="ff2b5-120">페이지 맨 위에 있는 **SQL Server 2012 MDS(Master Data Services)** 를 클릭 하 여 **마스터 데이터 관리자** 의 기본 페이지로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-120">Switch to the main page of **Master Data Manager** by clicking **SQL Server 2012 Master Data Services** at the top of the page.</span></span>  
  
11. <span data-ttu-id="ff2b5-121">**탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-121">Click **Explorer**.</span></span>  
  
12. <span data-ttu-id="ff2b5-122">**계층** 위로 마우스를 이동 하 고 **파생: SuppliersInState**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-122">Hover the mouse over **Hierarchies** and click **Derived:SuppliersInState**.</span></span>  
  
     <span data-ttu-id="ff2b5-123">![계층 - Derived:SuppliersInState 메뉴](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "계층 - Derived:SuppliersInState 메뉴")</span><span class="sxs-lookup"><span data-stu-id="ff2b5-123">![Hierarchies - Derived:SuppliersInState Menu](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-06.jpg "Hierarchies - Derived:SuppliersInState Menu")</span></span>  
  
13. <span data-ttu-id="ff2b5-124">**트리 뷰에서** 모든 **상태** 노드를 클릭 하면 오른쪽 창에 해당 주 공급자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff2b5-124">Click on any **state** node in the **tree view** and you should see the suppliers in that state in the right pane.</span></span>  
  
     <span data-ttu-id="ff2b5-125">![탐색기의 파생 계층](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "탐색기의 파생 계층")</span><span class="sxs-lookup"><span data-stu-id="ff2b5-125">![Derived Hierarchy in Explorer](../../2014/tutorials/media/et-creatingaderivedhierarchyusingmdm-07.jpg "Derived Hierarchy in Explorer")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="ff2b5-126">다음 단계</span><span class="sxs-lookup"><span data-stu-id="ff2b5-126">Next Step</span></span>  
 [<span data-ttu-id="ff2b5-127">5단원: SSIS를 사용하여 정리 및 일치 자동화</span><span class="sxs-lookup"><span data-stu-id="ff2b5-127">Lesson 5: Automating the Cleansing and Matching using SSIS</span></span>](../../2014/tutorials/lesson-5-automating-the-cleansing-and-matching-using-ssis.md)  
  
  
