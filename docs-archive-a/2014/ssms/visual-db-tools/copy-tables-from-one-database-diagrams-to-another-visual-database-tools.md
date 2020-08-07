---
title: 한 데이터베이스 다이어그램에서 다른 다이어그램으로 테이블 복사 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- duplicating tables
ms.assetid: 155a4f09-9321-4887-a7d4-aa2ce6b51277
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7e90c8f324e80f7c59674def06a77e93a5bf0cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727771"
---
# <a name="copy-tables-from-one-database-diagrams-to-another-visual-database-tools"></a><span data-ttu-id="c26e7-102">한 데이터베이스 다이어그램에서 다른 다이어그램으로 테이블 복사(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c26e7-102">Copy Tables from One Database Diagrams to Another (Visual Database Tools)</span></span>
  <span data-ttu-id="c26e7-103">같은 데이터베이스의 한 데이터베이스 다이어그램에서 다른 데이터베이스 다이어그램으로 테이블을 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-103">You can copy a table from one database diagram to another in the same database.</span></span>  
  
 <span data-ttu-id="c26e7-104">한 데이터베이스 다이어그램에서 다른 다이어그램으로 테이블을 복사하면 다른 다이어그램에는 그 테이블에 대한 참조만 추가되며</span><span class="sxs-lookup"><span data-stu-id="c26e7-104">Copying a table from one database diagram to another diagram adds a reference to the table in the second diagram.</span></span> <span data-ttu-id="c26e7-105">데이터베이스에 테이블이 복제되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-105">The table is not duplicated in your database.</span></span> <span data-ttu-id="c26e7-106">예를 들어 한 데이터베이스 다이어그램에서 다른 다이어그램으로 `authors` 테이블을 복사하면 각 다이어그램은 데이터베이스에 있는 같은 `authors` 테이블을 참조하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-106">For example, if you copy the `authors` table from one database diagram to another, each diagram references the same `authors` table in the database.</span></span>  
  
### <a name="to-copy-a-table-from-another-database-diagram"></a><span data-ttu-id="c26e7-107">다른 데이터베이스 다이어그램으로부터 테이블을 복사하려면</span><span class="sxs-lookup"><span data-stu-id="c26e7-107">To copy a table from another database diagram</span></span>  
  
1.  <span data-ttu-id="c26e7-108">복사할 테이블이 있는 데이터베이스에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-108">Make sure you are connected to the database whose table you want to copy.</span></span>  
  
2.  <span data-ttu-id="c26e7-109">원본 및 대상 데이터베이스 다이어그램을 열고 원본 다이어그램에서 대상 다이어그램으로 복사할 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-109">Open the source and target database diagrams and within the source diagram, select the table that you want to copy to the target diagram.</span></span>  
  
3.  <span data-ttu-id="c26e7-110">도구 모음의 **복사** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-110">Click the **Copy** button on the toolbar.</span></span> <span data-ttu-id="c26e7-111">이 단추를 클릭하면 선택한 테이블 정의가 클립보드에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-111">This action places the selected table definition on the Clipboard.</span></span>  
  
4.  <span data-ttu-id="c26e7-112">대상 다이어그램으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-112">Switch to the target diagram.</span></span> <span data-ttu-id="c26e7-113">이 다이어그램은 원본 다이어그램과 같은 데이터베이스에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-113">This diagram must be in the same database as the source diagram.</span></span>  
  
5.  <span data-ttu-id="c26e7-114">도구 모음에 있는 **붙여넣기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-114">Click the **Paste** button on the toolbar.</span></span> <span data-ttu-id="c26e7-115">클립보드 내용이 새 위치에 나타나고 다른 위치를 클릭할 때까지 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-115">The Clipboard contents appear at the new location and remain highlighted until you click elsewhere.</span></span> <span data-ttu-id="c26e7-116">대상 다이어그램에서 선택한 테이블과 다른 테이블 사이에 관계가 있으면 관계 선이 자동으로 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-116">If relationships exist between the selected tables and other tables in the target diagram, relationship lines are automatically drawn.</span></span>  
  
 <span data-ttu-id="c26e7-117">어느 한 쪽 다이어그램에서 테이블을 편집하면 변경 내용은 두 다이어그램에 모두 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-117">When you edit the table in either diagram, your changes are reflected in both diagrams.</span></span> <span data-ttu-id="c26e7-118">마찬가지로 어느 한 쪽 다이어그램에서 테이블을 저장하면 해당 테이블은 더 이상 두 다이어그램 모두에서 "수정"된 것으로 간주되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c26e7-118">Similarly, once you save the table in either diagram, the table is no longer considered "modified" in either diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26e7-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c26e7-119">See Also</span></span>  
 <span data-ttu-id="c26e7-120">[Visual Database Tools를 &#40;데이터베이스 다이어그램 작업&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="c26e7-120">[Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="c26e7-121">다이어그램에 테이블 추가&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="c26e7-121">Add Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](add-tables-to-diagrams-visual-database-tools.md)  
  
  
