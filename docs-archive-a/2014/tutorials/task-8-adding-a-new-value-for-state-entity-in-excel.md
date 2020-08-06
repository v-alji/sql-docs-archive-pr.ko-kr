---
title: '작업 8: Excel에서 State 엔터티에 대 한 새 값 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a763d76b-06a3-4d51-9614-01fc9fb1c158
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cace99419997e48088420c331a823cdf3639a3ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734644"
---
# <a name="task-8-adding-a-new-value-for-state-entity-in-excel"></a><span data-ttu-id="14fd6-102">태스크 8: Excel에서 State 엔터티에 새 값 추가</span><span class="sxs-lookup"><span data-stu-id="14fd6-102">Task 8: Adding a New Value for State Entity in Excel</span></span>
  <span data-ttu-id="14fd6-103">이 작업에서는 Excel에서 State 엔터티에 대한 값을 추가하고 변경 내용을 MDS 서버에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-103">In this task, you add a value for the State entity in Excel and publish the change to the MDS server.</span></span>  
  
1.  <span data-ttu-id="14fd6-104">맨 아래에 있는 새로 만들기 탭을 클릭 하 여 Excel에서 **작업 시트** 를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-104">Add a **work sheet** in Excel by clicking the new tab at the bottom.</span></span>  
  
     <span data-ttu-id="14fd6-105">![Excel - 새 워크시트 탭](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - 새 워크시트 탭")</span><span class="sxs-lookup"><span data-stu-id="14fd6-105">![Excel - New Worksheet Tab](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-01.jpg "Excel - New Worksheet Tab")</span></span>  
  
2.  <span data-ttu-id="14fd6-106">**Excel**의 메뉴에서 **마스터 데이터** 탭을 클릭 한 다음 리본 메뉴에서 **탐색기 표시** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-106">In **Excel**, click the **Master Data** tab on the menu, and then click **Show Explorer** on the ribbon.</span></span>  
  
3.  <span data-ttu-id="14fd6-107">**마스터 데이터 탐색기**에서 **모델**에 대해 **Suppliers** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-107">In the **Master Data Explorer**, select **Suppliers** for **Model**.</span></span> <span data-ttu-id="14fd6-108">엔터티 목록에 **공급자** 와 **상태** 라는 두 엔터티가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-108">You should see two entities: **Supplier** and **State** in the entity list.</span></span>  
  
4.  <span data-ttu-id="14fd6-109">목록에서 **상태** 를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-109">Double-click **State** in the list.</span></span> <span data-ttu-id="14fd6-110">MDS의 **State** 엔터티에 대 한 모든 멤버가 워크시트에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-110">All the members of the **State** entity from MDS should be displayed in the worksheet.</span></span>  
  
5.  <span data-ttu-id="14fd6-111">이제 **이름** 에는 **북쪽 Carolina** , **코드** **의 경우에는** 다음 값으로 끝에 행을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-111">Now, add a row at the end with the following values: **North Carolina** for **Name** and **NC** for **Code**.</span></span> <span data-ttu-id="14fd6-112">색 구분에 따라 새 레코드/업데이트된 레코드가 다른 레코드와 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-112">The color coding differentiates any new/updated records from the other records.</span></span>  
  
     <span data-ttu-id="14fd6-113">![Excel - 미국에 North Carolina 추가](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel - 미국에 North Carolina 추가")</span><span class="sxs-lookup"><span data-stu-id="14fd6-113">![Excel - Add North Carolina to States](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-02.jpg "Excel - Add North Carolina to States")</span></span>  
  
6.  <span data-ttu-id="14fd6-114">리본에서 **게시** 를 클릭 하 여 변경 내용을 MDS에 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-114">Click **Publish** on the ribbon to publish the change to MDS.</span></span>  
  
     <span data-ttu-id="14fd6-115">![Excel - 마스터 데이터 탭의 게시 단추](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel - 마스터 데이터 탭의 게시 단추")</span><span class="sxs-lookup"><span data-stu-id="14fd6-115">![Excel - Publish Button on Master Data Tab](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-03.jpg "Excel - Publish Button on Master Data Tab")</span></span>  
  
7.  <span data-ttu-id="14fd6-116">**게시 및 주석** 대화 상자에서 **모든 변경 내용에 동일한 주석 사용** 이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-116">On the **Publish and Annotate** dialog box, notice that the **Use same annotation for all changes** is selected.</span></span> <span data-ttu-id="14fd6-117">여기에서 모든 변경 내용에 대해 단일 주석을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-117">You can enter a single annotation for all the changes here.</span></span>  
  
8.  <span data-ttu-id="14fd6-118">변경 **내용을 검토 하 고 개별적으로 주석 제공** 옵션을 선택 하 여 각 변경 내용에 대 한 주석을 제공 합니다 (이 경우에만).</span><span class="sxs-lookup"><span data-stu-id="14fd6-118">Select **Review changes and provide annotations individually** option to provide annotation for each change (in this case, only one).</span></span>  
  
     <span data-ttu-id="14fd6-119">![Excel - 게시 및 주석 달기 대화 상자](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel - 게시 및 주석 달기 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="14fd6-119">![Excel - Publish and Annotate Dialog Box](../../2014/tutorials/media/et-addinganewvalueforstateentityinexcel-04.jpg "Excel - Publish and Annotate Dialog Box")</span></span>  
  
9. <span data-ttu-id="14fd6-120">**게시** 를 클릭 하 여 데이터를 MDS에 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-120">Click **Publish** to publish data to MDS.</span></span>  
  
10. <span data-ttu-id="14fd6-121">**북쪽 Carolina** 이 있는 행에 대 한 **색 구분** 이 현재 다른 레코드와 **동일 합니다.**</span><span class="sxs-lookup"><span data-stu-id="14fd6-121">Notice that **color coding** for the row with **North Carolina** as the **State** is same as other records now.</span></span>  
  
11. <span data-ttu-id="14fd6-122">**선택 사항:** **마스터 데이터 관리자**에서 **탐색기** 를 사용 하 여 새 멤버 (NC)가 **상태** 엔터티에 추가 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-122">**Optional:** Verify that the new member (NC) is added to the **State** entity by using the **Explorer** in **Master Data Manager**.</span></span>  
  
12. <span data-ttu-id="14fd6-123">Excel에서 아래쪽의 **상태** 워크시트를 마우스 오른쪽 단추로 클릭 하 고 **삭제** 를 클릭 하 여 워크시트를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-123">In Excel, right-click the **State** worksheet at the bottom, and click **Delete** to delete the worksheet.</span></span> <span data-ttu-id="14fd6-124">워크시트를 삭제해도 MDS 서버에서는 데이터가 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14fd6-124">Deleting the worksheet does not delete any data from the MDS server.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="14fd6-125">다음 단계</span><span class="sxs-lookup"><span data-stu-id="14fd6-125">Next Step</span></span>  
 [<span data-ttu-id="14fd6-126">태스크 9: 마스터 데이터 관리자를 사용하여 파생 계층 만들기</span><span class="sxs-lookup"><span data-stu-id="14fd6-126">Task 9: Creating a Derived Hierarchy using Master Data Manager</span></span>](../../2014/tutorials/task-9-creating-a-derived-hierarchy-using-master-data-manager.md)  
  
  
