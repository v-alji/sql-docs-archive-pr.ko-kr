---
title: 옵션 (디자이너-테이블 및 데이터베이스 디자이너 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Designers.Table_Designer
ms.assetid: b43f4b97-17b9-4004-a824-f77b9e145741
author: stevestein
ms.author: sstein
ms.openlocfilehash: d8a1218b4ea1ae9c6f9cf734bb33a2a4bebcb167
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653099"
---
# <a name="options-designers-table-and-database-designers-page"></a><span data-ttu-id="4f68b-102">옵션 (디자이너-테이블 및 데이터베이스 디자이너 페이지)</span><span class="sxs-lookup"><span data-stu-id="4f68b-102">Options (Designers-Table and Database Designers Page)</span></span>
  <span data-ttu-id="4f68b-103">이 페이지를 사용하여 디자이너의 기본 동작을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-103">Use this page to determine the default behavior of the designer.</span></span> <span data-ttu-id="4f68b-104">이 설정에 액세스하려면 **도구** 메뉴에서 **옵션**을 클릭하고 **디자이너** 폴더를 확장한 다음 **테이블 디자이너**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-104">To access the settings, on the **Tools** menu, click **Options**, expand the **Designers** folder, and click **Table Designer**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="4f68b-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="4f68b-105">UI element list</span></span>  
 <span data-ttu-id="4f68b-106">**테이블 디자이너 업데이트에 대한 연결 문자열 제한 시간 값 재정의**</span><span class="sxs-lookup"><span data-stu-id="4f68b-106">**Override connection string time-out value for table designer updates**</span></span>  
 <span data-ttu-id="4f68b-107">테이블 디자이너의 동작에 대해 새 제한 시간 값을 설정하도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-107">Permits a new time-out value to be set for the actions of the table designer.</span></span> <span data-ttu-id="4f68b-108">이 옵션은 테이블 디자이너가 수정하는 데 시간이 많이 걸리는 대형 테이블에 대한 작업을 수행하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-108">This can be useful when the table designer affects a large table and requires extra time to complete the table modification.</span></span>  
  
 <span data-ttu-id="4f68b-109">**트랜잭션 제한 시간**</span><span class="sxs-lookup"><span data-stu-id="4f68b-109">**Transaction time-out after**</span></span>  
 <span data-ttu-id="4f68b-110">테이블 디자이너에 대한 제한 시간 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-110">Sets a time-out value for the table designer.</span></span>  
  
 <span data-ttu-id="4f68b-111">**변경 스크립트 자동 생성**</span><span class="sxs-lookup"><span data-stu-id="4f68b-111">**Auto generate change scripts**</span></span>  
 <span data-ttu-id="4f68b-112">테이블 디자이너에서 정의된 변경 내용을 구현하는 스크립트를 자동으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-112">Automatically creates a script to implement the changes defined in the table designer.</span></span>  
  
 <span data-ttu-id="4f68b-113">**Null 기본 키 경고**</span><span class="sxs-lookup"><span data-stu-id="4f68b-113">**Warn on null primary keys**</span></span>  
 <span data-ttu-id="4f68b-114">기본 키로 선택한 필드에 Null 값이 포함될 수 있는 경우에 경고 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-114">Provides a warning dialog box when a field that is selected for a primary key can contain null values.</span></span>  
  
 <span data-ttu-id="4f68b-115">**차이점 발견 경고**</span><span class="sxs-lookup"><span data-stu-id="4f68b-115">**Warn about difference detection**</span></span>  
 <span data-ttu-id="4f68b-116">이 확인란을 선택하면 변경 내용을 저장할 때 현재 변경 내용과 다른 사용자의 변경 내용 간 충돌 사항이 모두 메시지 상자에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-116">If you check this box, when you save the changes, a message box will list any conflicts between your changes and changes that were made by another user.</span></span>  
  
 <span data-ttu-id="4f68b-117">**영향을 받는 테이블 경고**</span><span class="sxs-lookup"><span data-stu-id="4f68b-117">**Warn about tables affected**</span></span>  
 <span data-ttu-id="4f68b-118">동작 대상 테이블을 표시하고 사용자의 확인을 받는 경고 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-118">Provides a warning dialog box that lists the tables to be affected by the action and prompts for confirmation.</span></span>  
  
 <span data-ttu-id="4f68b-119">**테이블을 다시 만들어야 하는 변경 내용 저장 사용 안 함**</span><span class="sxs-lookup"><span data-stu-id="4f68b-119">**Prevent saving changes that require table re-creation**</span></span>  
 <span data-ttu-id="4f68b-120">테이블을 다시 만들어야 하는 변경 내용을 사용자가 저장할 수 없게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-120">Prevents a user from making changes that require re-creating the table.</span></span> <span data-ttu-id="4f68b-121">다음 동작을 수행하려면 테이블을 다시 만들어야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-121">The following actions might require a table to be re-created:</span></span>  
  
-   <span data-ttu-id="4f68b-122">테이블의 중간에 새 열 추가</span><span class="sxs-lookup"><span data-stu-id="4f68b-122">Adding a new column to the middle of the table</span></span>  
  
-   <span data-ttu-id="4f68b-123">열 삭제</span><span class="sxs-lookup"><span data-stu-id="4f68b-123">Dropping a column</span></span>  
  
-   <span data-ttu-id="4f68b-124">열의 Null 허용 여부 변경</span><span class="sxs-lookup"><span data-stu-id="4f68b-124">Changing column nullability</span></span>  
  
-   <span data-ttu-id="4f68b-125">열의 순서 변경</span><span class="sxs-lookup"><span data-stu-id="4f68b-125">Changing the order of the columns</span></span>  
  
-   <span data-ttu-id="4f68b-126">열의 데이터 형식 변경</span><span class="sxs-lookup"><span data-stu-id="4f68b-126">Changing the data type of a column</span></span>  
  
 <span data-ttu-id="4f68b-127">**기본 테이블 뷰**</span><span class="sxs-lookup"><span data-stu-id="4f68b-127">**Default table view**</span></span>  
 <span data-ttu-id="4f68b-128">다음과 같이 디자이너에서 테이블을 표시하는 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-128">Select the way you want to see tables in the designers:</span></span>  
  
-   <span data-ttu-id="4f68b-129">**Standard**</span><span class="sxs-lookup"><span data-stu-id="4f68b-129">**Standard**</span></span>  
  
     <span data-ttu-id="4f68b-130">테이블 머리글, 모든 열 이름, 데이터 형식 및 Null 허용 설정을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-130">Shows the table header, all column names, data types, and the Allow Nulls setting.</span></span>  
  
-   <span data-ttu-id="4f68b-131">**열 이름**</span><span class="sxs-lookup"><span data-stu-id="4f68b-131">**Column Names**</span></span>  
  
     <span data-ttu-id="4f68b-132">열 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-132">Shows the column names.</span></span>  
  
-   <span data-ttu-id="4f68b-133">**Key**</span><span class="sxs-lookup"><span data-stu-id="4f68b-133">**Key**</span></span>  
  
     <span data-ttu-id="4f68b-134">테이블 머리글과 기본 키 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-134">Shows the table header and the primary key columns.</span></span>  
  
-   <span data-ttu-id="4f68b-135">**테이블 이름만**</span><span class="sxs-lookup"><span data-stu-id="4f68b-135">**Name Only**</span></span>  
  
     <span data-ttu-id="4f68b-136">테이블 이름이 있는 테이블 머리글만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-136">Shows only the table header with it's name.</span></span>  
  
-   <span data-ttu-id="4f68b-137">**Custom**</span><span class="sxs-lookup"><span data-stu-id="4f68b-137">**Custom**</span></span>  
  
     <span data-ttu-id="4f68b-138">표시할 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-138">Allows you to choose which columns to view.</span></span>  
  
 <span data-ttu-id="4f68b-139">**새 다이어그램에서 [테이블 추가] 대화 상자 시작**</span><span class="sxs-lookup"><span data-stu-id="4f68b-139">**Launch add table dialog on new diagram**</span></span>  
 <span data-ttu-id="4f68b-140">디자이너가 열리면 자동으로 **테이블 추가** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="4f68b-140">Automatically opens the **Add Table** dialog box when the designers open.</span></span>  
  
  
