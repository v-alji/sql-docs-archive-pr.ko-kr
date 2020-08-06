---
title: CDC 인스턴스에 테이블 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- addTabs
ms.assetid: ad260e19-c021-4035-9311-c02fc96ceaea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: edcd84db9e3c464334d407987cb3567f78edd44e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728644"
---
# <a name="add-tables-to-a-cdc-instance"></a><span data-ttu-id="b79e4-102">CDC 인스턴스에 테이블 추가</span><span class="sxs-lookup"><span data-stu-id="b79e4-102">Add Tables to a CDC Instance</span></span>
  <span data-ttu-id="b79e4-103">테이블 선택 대화 상자를 사용하여 Oracle 원본에서 CDC 인스턴스로 다른 테이블을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-103">Use the Table Selection dialog box to add additional tables from the Oracle source to the CDC instance.</span></span> <span data-ttu-id="b79e4-104">선택한 테이블이 속성 편집기의 **테이블** 탭에 있는 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-104">The tables selected are added to the list in the **Tables** tab of the Properties editor.</span></span>  
  
 <span data-ttu-id="b79e4-105">기본적으로 이 대화 상자의 테이블 목록에는 테이블이 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-105">By default, no tables are included in the list of tables in this dialog box.</span></span> <span data-ttu-id="b79e4-106">**(모두 선택)** 확인란을 선택하거나 특정 테이블을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-106">You can select the **(Select All)** check box or search for specific tables.</span></span>  
  
 <span data-ttu-id="b79e4-107">**특정 테이블을 검색하려면**</span><span class="sxs-lookup"><span data-stu-id="b79e4-107">**To search for specific tables**</span></span>  
 <span data-ttu-id="b79e4-108">다음과 같이 검색 조건을 입력한 다음 **검색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-108">Enter search criteria as follows, and then click **Search**:</span></span>  
  
-   <span data-ttu-id="b79e4-109">**스키마**: 목록에서 데이터베이스 스키마를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-109">**Schema**: Select a database schema from the list.</span></span> <span data-ttu-id="b79e4-110">해당 스키마가 있는 테이블만 목록에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-110">Only tables that have that schema will be included in the list.</span></span>  
  
-   <span data-ttu-id="b79e4-111">**테이블 이름 패턴**: 임의의 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-111">**Table Name Pattern**: Enter any string of characters.</span></span> <span data-ttu-id="b79e4-112">입력된 문자열을 포함하는 테이블만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-112">Only tables that include the character string entered are displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b79e4-113">이러한 필드 중 하나 또는 모두에 조건을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-113">You can enter criteria in one or both of these fields.</span></span>  
  
-   <span data-ttu-id="b79e4-114">**처음 1,000개의 일치하는 테이블 표시**: 기본적으로 이 확인란은 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-114">**Display first 1000 matching tables**: By default this check box is selected.</span></span> <span data-ttu-id="b79e4-115">이 옵션은 처음 1000개의 일치하는 테이블로 표시를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-115">It limits the display to the first 1000 matching tables.</span></span> <span data-ttu-id="b79e4-116">이 확인란을 선택하지 않으면 조건과 일치하는 모든 테이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-116">If you clear the check box, all tables that match the criteria are displayed.</span></span> <span data-ttu-id="b79e4-117">따라서 많은 테이블이 있는 경우 목록을 표시하는 데 많은 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-117">If there are a large number of tables, it may take a long time to display the list.</span></span>  
  
 <span data-ttu-id="b79e4-118">**CDC 인스턴스에 포함할 테이블을 선택하려면**</span><span class="sxs-lookup"><span data-stu-id="b79e4-118">**To select tables to include in the CDC instance**</span></span>  
 <span data-ttu-id="b79e4-119">포함할 테이블 옆의 확인란을 클릭한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-119">Click the check box next to any of the tables you want to include, and then click **Add**.</span></span> <span data-ttu-id="b79e4-120">테이블이 새 인스턴스 마법사의 **테이블 및 열 선택** 페이지에 있는 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-120">The tables are added to the list in the New Instance Wizard **Select Tables and Columns** page.</span></span>  
  
 <span data-ttu-id="b79e4-121">테이블을 추가하지 않고 대화 상자를 닫으려면 **닫기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-121">Click **Close** to close the dialog box without adding any tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b79e4-122">지원되지 않는 데이터 형식을 포함하는 테이블을 선택한 경우 오류 메시지가 표시되고 테이블은 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-122">If you select a table that includes a non-supported data type, you will see an error message and the table will not be included.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b79e4-123">뷰어에서 테이블 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-123">You can view the list of tables in the viewer.</span></span> <span data-ttu-id="b79e4-124">뷰어를 사용할 때 정보는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-124">When using the viewer the information is read only.</span></span> <span data-ttu-id="b79e4-125">또한 뷰어에는 테이블에서 캡처된 열 목록이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b79e4-125">The viewer also includes a list of the captured columns in the table.</span></span> <span data-ttu-id="b79e4-126">뷰어에 액세스하는 방법은 [How to Manage a CDC Instance](manage-a-cdc-instance.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b79e4-126">For information on how to access the viewer, see [How to Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b79e4-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b79e4-127">See Also</span></span>  
 <span data-ttu-id="b79e4-128">[CDC 인스턴스 속성을 편집하는 방법](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="b79e4-128">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 <span data-ttu-id="b79e4-129">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="b79e4-129">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="b79e4-130">변경 내용을 캡처할 Oracle 테이블 선택</span><span class="sxs-lookup"><span data-stu-id="b79e4-130">Select Oracle Tables for Capturing Changes</span></span>](select-oracle-tables-for-capturing-changes.md)  
  
  
