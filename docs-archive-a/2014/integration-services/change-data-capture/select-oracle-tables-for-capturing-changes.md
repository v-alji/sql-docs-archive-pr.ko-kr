---
title: 변경 내용을 캡처할 Oracle 테이블 선택 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- selOraTabDia
ms.assetid: 2e295dc8-999d-4c4d-96cc-1519674b47a4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e9064789dce83ff7d3917ed026c861743142e048
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735511"
---
# <a name="select-oracle-tables-for-capturing-changes"></a><span data-ttu-id="97953-102">변경 내용을 캡처할 Oracle 테이블 선택</span><span class="sxs-lookup"><span data-stu-id="97953-102">Select Oracle Tables for Capturing Changes</span></span>
  <span data-ttu-id="97953-103">이 대화 상자를 사용하여 CDC 인스턴스에 포함되는 테이블을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97953-103">Use this dialog box to select the tables that are included in the CDC instance.</span></span> <span data-ttu-id="97953-104">선택된 테이블은 새 인스턴스 마법사의 **테이블 및 열 선택** 페이지의 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="97953-104">The tables selected are added to the list in the **Select Tables and Columns** page of the New Instance wizard.</span></span> <span data-ttu-id="97953-105">이 대화 상자에서 다음과 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97953-105">You can do the following in this dialog box.</span></span>  
  
 <span data-ttu-id="97953-106">기본적으로 이 대화 상자의 테이블 목록에는 테이블이 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97953-106">By default, no tables are included in the list of tables in this dialog box.</span></span> <span data-ttu-id="97953-107">확인란 열의 맨 위에 있는 확인란을 선택하여 모든 테이블을 선택하거나 특정 테이블을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97953-107">You can select the check box at the top of the check box column to select all of the tables or search for specific tables.</span></span>  
  
 <span data-ttu-id="97953-108">**특정 테이블을 검색하려면**</span><span class="sxs-lookup"><span data-stu-id="97953-108">**To search for specific tables**</span></span>  
 <span data-ttu-id="97953-109">다음과 같이 검색 조건을 입력한 다음 **검색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97953-109">Enter search criteria as follows, and then click **Search**:</span></span>  
  
-   <span data-ttu-id="97953-110">**스키마**: 목록에서 데이터베이스 스키마를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="97953-110">**Schema**: Select a database schema from the list.</span></span> <span data-ttu-id="97953-111">해당 스키마가 있는 테이블만 목록에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="97953-111">Only tables that have that schema will be included in the list.</span></span>  
  
-   <span data-ttu-id="97953-112">**테이블 이름 패턴**: 임의의 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="97953-112">**Table Name Pattern**: Enter any string of characters.</span></span> <span data-ttu-id="97953-113">입력된 문자열을 포함하는 테이블만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="97953-113">Only tables that include the character string entered are displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97953-114">이러한 필드 중 하나 또는 모두에 조건을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97953-114">You can enter criteria in one or both of these fields.</span></span>  
  
-   <span data-ttu-id="97953-115">**처음 1,000개의 일치하는 테이블 표시**: 기본적으로 이 확인란은 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97953-115">**Display first 1000 matching tables**: By default this check box is selected.</span></span> <span data-ttu-id="97953-116">이 옵션은 처음 1000개의 일치하는 테이블로 표시를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="97953-116">It limits the display to the first 1000 matching tables.</span></span> <span data-ttu-id="97953-117">이 확인란을 선택하지 않으면 조건과 일치하는 모든 테이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="97953-117">If you clear the check box, all tables that match the criteria are displayed.</span></span> <span data-ttu-id="97953-118">따라서 많은 테이블이 있는 경우 목록을 표시하는 데 많은 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97953-118">If there are a large number of tables, it may take a long time to display the list.</span></span>  
  
 <span data-ttu-id="97953-119">**CDC 인스턴스에 포함할 테이블을 선택하려면**</span><span class="sxs-lookup"><span data-stu-id="97953-119">**To select tables to include in the CDC instance**</span></span>  
 <span data-ttu-id="97953-120">포함할 테이블 옆의 확인란을 클릭한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97953-120">Click the check box next to any of the tables you want to include, and then click **Add**.</span></span> <span data-ttu-id="97953-121">테이블이 새 인스턴스 마법사의 **테이블 및 열 선택** 페이지에 있는 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="97953-121">The tables are added to the list in the New Instance Wizard **Select Tables and Columns** page.</span></span>  
  
 <span data-ttu-id="97953-122">다른 테이블을 추가하지 않고 대화 상자를 닫으려면 **닫기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97953-122">Click **Close** to close the dialog box without adding any additional tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97953-123">지원되지 않는 데이터 형식을 포함하는 테이블을 선택한 경우 오류 메시지가 표시되고 테이블은 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97953-123">If you select a table that includes a non-supported data type, you will see an error message and the table will not be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97953-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97953-124">See Also</span></span>  
 <span data-ttu-id="97953-125">[SQL Server 변경 데이터베이스 인스턴스를 만드는 방법](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="97953-125">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="97953-126">Oracle 테이블 및 열 선택</span><span class="sxs-lookup"><span data-stu-id="97953-126">Select Oracle Tables and Columns</span></span>](select-oracle-tables-and-columns.md)  
  
  
