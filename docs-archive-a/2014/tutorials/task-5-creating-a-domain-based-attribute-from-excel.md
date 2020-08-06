---
title: '태스크 5: Excel에서 도메인 기반 특성 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 07cbc624-2c6b-4568-96e4-f18663a05d80
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b866478150fb4c06a3c4ea1ee6c227527f963219
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732203"
---
# <a name="task-5-creating-a-domain-based-attribute-from-excel"></a><span data-ttu-id="2ec47-102">태스크 5: Excel에서 도메인 기반 특성 만들기</span><span class="sxs-lookup"><span data-stu-id="2ec47-102">Task 5: Creating a Domain-Based Attribute from Excel</span></span>
  <span data-ttu-id="2ec47-103">이 태스크에서는 **공급자** 엔터티의 **State** 특성을 **도메인 기반 특성**으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec47-103">In this task, you convert the **State** attribute of the **Supplier** entity as a **domain-based attribute**.</span></span> <span data-ttu-id="2ec47-104">State 특성을 도메인 기반으로 구성한 후 MDS에 게시 하면 **상태** 라는 새 엔터티가 열의 모든 값을 사용 하 여 mds 서버에 생성 되 고 **공급자** 엔터티의 **state** 특성은 **state** 엔터티의 값으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="2ec47-104">After you configure the State attribute to be a domain-based one and publish it to MDS, a new entity named **State** will be created on MDS server with all the values in the column and the **State** attribute of the **Supplier** entity will be populated with values from the **State** entity.</span></span> <span data-ttu-id="2ec47-105">이제 **Suppliers** **모델에** **는 공급자 엔터티의** **state** 특성과 **state 엔터티에 종속** 된 도메인 기반 **특성이 있는 두** 개의 엔터티가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec47-105">Now, the **Suppliers** model should have two entities: **Supplier** and **State** where the **State** attribute of the **Supplier** entity is a domain-based attribute that depends on **State** entity.</span></span>  
  
1.  <span data-ttu-id="2ec47-106">**정리 하 고 일치** 하는 Suppliers.xlsx열어 놓은 **Excel** 창으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec47-106">Switch to **Excel** window that has **Cleansed and Matched Suppliers.xlsx** open.</span></span>  
  
2.  <span data-ttu-id="2ec47-107">리본에서 **새로 고침** 단추를 클릭 하 여 MDS에서 최신 업데이트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2ec47-107">Click **Refresh** button on the ribbon to get the latest updates from MDS.</span></span> <span data-ttu-id="2ec47-108">선택적 **작업 4**를 수행한 경우에는 두 개 이상의 레코드가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ec47-108">You should see the two more records if you have performed the optional **Task 4**.</span></span>  
  
3.  <span data-ttu-id="2ec47-109">**머리글 행**에서 열 이름 **상태** ( **I1**셀)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec47-109">Click column name **State** (cell **I1**) in the **header row**.</span></span>  
  
     <span data-ttu-id="2ec47-110">![Excel - 특성 속성 단추](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - 특성 속성 단추")</span><span class="sxs-lookup"><span data-stu-id="2ec47-110">![Excel - Attribute Properties Button](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-01.jpg "Excel - Attribute Properties Button")</span></span>  
  
4.  <span data-ttu-id="2ec47-111">리본에서 **특성 속성** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec47-111">Click **Attribute Properties** on the ribbon.</span></span>  
  
5.  <span data-ttu-id="2ec47-112">**특성 속성** 대화 상자에서 **특성 유형에**대 한 **제한 목록 (도메인 기반)** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec47-112">In the **Attribute Properties** dialog box, select **Constrained list (Domain-based)** for the **Attribute type**.</span></span>  
  
6.  <span data-ttu-id="2ec47-113">**새 엔터티 이름** 에 **상태** 를 입력 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ec47-113">Type **State** for the **New entity name** and click **OK**.</span></span>  
  
     <span data-ttu-id="2ec47-114">![Excel - 특성 속성 대화 상자](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - 특성 속성 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="2ec47-114">![Excel - Attribute Properties Dialog Box](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-02.jpg "Excel - Attribute Properties Dialog Box")</span></span>  
  
7.  <span data-ttu-id="2ec47-115">이제 Excel에서는 **상태** 열에서 값을 클릭 하면 **아래쪽 화살표가** 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ec47-115">Now, in Excel, you should see **down arrow** when you click any value in the **State** column.</span></span> <span data-ttu-id="2ec47-116">필요에 따라 드롭 다운 목록을 사용해서 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ec47-116">You can change the value by using the drop-down list if you need.</span></span>  
  
     <span data-ttu-id="2ec47-117">![Excel - 상태가 있는 드롭다운 목록](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - 상태가 있는 드롭다운 목록")</span><span class="sxs-lookup"><span data-stu-id="2ec47-117">![Excel - Drop Down List with States](../../2014/tutorials/media/et-creatingadomainbasedattributefromexcel-03.jpg "Excel - Drop Down List with States")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="2ec47-118">다음 단계</span><span class="sxs-lookup"><span data-stu-id="2ec47-118">Next Step</span></span>  
 [<span data-ttu-id="2ec47-119">태스크 6: 마스터 데이터 관리자를 사용하여 도메인 기반 특성이 생성되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="2ec47-119">Task 6: Verify that the Domain-Based Attribute is Created using Master Data Manager</span></span>](../../2014/tutorials/task-6-verify-domain-based-attribute-master-data-manager.md)  
  
  
