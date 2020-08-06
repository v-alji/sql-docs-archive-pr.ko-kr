---
title: 코드 개요
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], outlining code
- Query Editor [SQL Server Management Studio], hiding code
ms.assetid: 556c7dfe-7bc8-4cab-a36f-2b753a05d3f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 0a142ca8fbdcdfcfbfd1b71de06c0b0fd4c5339c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649453"
---
# <a name="code-outlining"></a><span data-ttu-id="946dd-102">코드 개요</span><span class="sxs-lookup"><span data-stu-id="946dd-102">Code Outlining</span></span>
  <span data-ttu-id="946dd-103">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 쿼리를 편집할 때 개요 기능을 사용하여 코드를 필요에 따라 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-103">You can use the outlining feature in the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] query editors to selectively hide code when you edit queries.</span></span> <span data-ttu-id="946dd-104">이 기능을 사용하면 특히 큰 쿼리 파일에서 작업 중인 코드를 쉽게 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-104">This enables you to more easily view the code you are working on, especially in large query files.</span></span>

## <a name="outlining-overview"></a><span data-ttu-id="946dd-105">개요 기능 개요</span><span class="sxs-lookup"><span data-stu-id="946dd-105">Outlining Overview</span></span>
 <span data-ttu-id="946dd-106">기본적으로 쿼리 편집기 창을 열 때 모든 코드가 표시되지만</span><span class="sxs-lookup"><span data-stu-id="946dd-106">By default, all code is visible when you open a query editor window.</span></span> <span data-ttu-id="946dd-107">필요에 따라 코드 영역을 축소하여 코드를 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-107">Regions of the code can be collapsed to hide it from view.</span></span> <span data-ttu-id="946dd-108">편집기 창 왼쪽 가장자리의 세로선에서 빼기 기호(-)가 있는 사각형은 축소 가능한 각 코드 영역의 시작 부분을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-108">A vertical line on the left edge of the editor window uses a square with a minus sign (-) to identify the start of each collapsible code region.</span></span> <span data-ttu-id="946dd-109">빼기 기호를 클릭하면 코드 영역의 텍스트는 3개의 마침표(...)가 포함된 상자로 대체되고 빼기 기호는 더하기 기호(+)로 변합니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-109">When you click a minus sign, the text of the code region is replaced with a box that contains three periods (...), and the minus sign changes to a plus sign (+).</span></span> <span data-ttu-id="946dd-110">더하기 기호를 클릭하면 축소된 코드가 나타나고 더하기 기호가 빼기 기호로 변합니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-110">When you click a plus sign, the collapsed code appears and the plus sign changes to a minus sign.</span></span> <span data-ttu-id="946dd-111">포인터를 3개의 마침표가 있는 상자 위로 이동하면 축소된 섹션의 코드를 보여 주는 도구 설명이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-111">When you move the pointer over a box that has three periods, a tooltip appears that shows the code in the collapsed section.</span></span>

## <a name="system-outline-regions"></a><span data-ttu-id="946dd-112">시스템 개요 영역</span><span class="sxs-lookup"><span data-stu-id="946dd-112">System Outline Regions</span></span>
 <span data-ttu-id="946dd-113">각 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 편집기에서는 기본 시스템 정의 개요 영역 집합을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-113">Each [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] editor generates a set of default, system-defined outline regions.</span></span>

 <span data-ttu-id="946dd-114">MDX 및 DMX 코드 편집기는 여러 줄로 된 각 문에 대한 개요 영역을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-114">The MDX and DMX code editors create outline regions for each multiline statement.</span></span> <span data-ttu-id="946dd-115">이것이 이러한 편집기에서 지원하는 유일한 개요 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-115">This is the only level of outlining that these editors support.</span></span>

### <a name="analysis-services-xmla-query-editor-regions"></a><span data-ttu-id="946dd-116">Analysis Services XMLA 쿼리 편집기 영역</span><span class="sxs-lookup"><span data-stu-id="946dd-116">Analysis Services XMLA Query Editor Regions</span></span>
 <span data-ttu-id="946dd-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA 쿼리 편집기는 여러 줄로 된 각 XML 특성에 대한 개요 영역을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-117">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA Query Editor generates an outline region for each multiline XML attribute.</span></span> <span data-ttu-id="946dd-118">중첩 태그에 대한 개요 영역은 중첩됩니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-118">The editor nests the outline regions for nested tags.</span></span> <span data-ttu-id="946dd-119">예를 들어 XMLA 편집기는 다음 문서에 대해 3개의 개요 영역을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-119">For example, the XMLA Editor creates three outline regions for the following document.</span></span>

 <span data-ttu-id="946dd-120">![개요를 보여 주는 XML 코드](../../database-engine/media/editoutlinexmlfull.gif "개요를 보여 주는 XML 코드")</span><span class="sxs-lookup"><span data-stu-id="946dd-120">![XML code showing outlining](../../database-engine/media/editoutlinexmlfull.gif "XML code showing outlining")</span></span>

 <span data-ttu-id="946dd-121">줄에서 빼기 기호를 클릭 하면 \<InnerTag> 다음 그림과 같이 InnerTag만 축소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-121">When you click the minus sign on the \<InnerTag> line, just the InnerTag is collapsed, as shown in the following illustration.</span></span>

 <span data-ttu-id="946dd-122">![내부 노드가 숨겨진 XML 코드](../../database-engine/media/editoutlinexmlinnercol.gif "내부 노드가 숨겨진 XML 코드")</span><span class="sxs-lookup"><span data-stu-id="946dd-122">![XML code with inner node hidden](../../database-engine/media/editoutlinexmlinnercol.gif "XML code with inner node hidden")</span></span>

 <span data-ttu-id="946dd-123">포인터를 3개의 마침표(...)가 있는 상자 위로 이동하면 다음 그림과 같이 축소된 영역의 코드가 도구 설명에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-123">When you move the pointer over the box that has the three periods (...), the code in the collapsed region appears in a tooltip, as shown in the following illustration.</span></span>

 <span data-ttu-id="946dd-124">![숨겨진 코드를 보여 주는 도구 설명을 포함하는 XML 코드](../../database-engine/media/editoutlinexmlmouse.gif "숨겨진 코드를 보여 주는 도구 설명을 포함하는 XML 코드")</span><span class="sxs-lookup"><span data-stu-id="946dd-124">![XML code with tooltip showing hidden code](../../database-engine/media/editoutlinexmlmouse.gif "XML code with tooltip showing hidden code")</span></span>

 <span data-ttu-id="946dd-125">줄에서 빼기 기호를 클릭 하면 \<MiddleTag> 다음 그림과 같이 MiddleTag 및 InnerTag가 모두 축소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-125">When you click the minus sign on the \<MiddleTag> line, both the MiddleTag and InnerTag are collapsed, as shown in the following illustration.</span></span>

 <span data-ttu-id="946dd-126">![내부 및 가운데 태그가 숨겨진 XML 코드](../../database-engine/media/editoutlinexmlmiddlecol.gif "내부 및 가운데 태그가 숨겨진 XML 코드")</span><span class="sxs-lookup"><span data-stu-id="946dd-126">![XML code with inner and middle tags hidden](../../database-engine/media/editoutlinexmlmiddlecol.gif "XML code with inner and middle tags hidden")</span></span>

 <span data-ttu-id="946dd-127">줄에서 빼기 기호를 클릭 하면 \<OuterTag> 다음 그림과 같이 세 줄이 모두 축소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-127">When you click the minus sign on the \<OuterTag> line, all three lines are collapsed, as shown in the following illustration.</span></span>

 <span data-ttu-id="946dd-128">![숨겨진 3개의 태그를 모두 보여 주는 XML 코드](../../database-engine/media/editoutlinexmloutercol.gif "숨겨진 3개의 태그를 모두 보여 주는 XML 코드")</span><span class="sxs-lookup"><span data-stu-id="946dd-128">![XML code showing all three tags hidden](../../database-engine/media/editoutlinexmloutercol.gif "XML code showing all three tags hidden")</span></span>

### <a name="database-engine-query-editor-regions"></a><span data-ttu-id="946dd-129">데이터베이스 엔진 쿼리 편집기 영역</span><span class="sxs-lookup"><span data-stu-id="946dd-129">Database Engine Query Editor Regions</span></span>
 <span data-ttu-id="946dd-130">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 쿼리 편집기는 다음 계층의 각 요소에 대한 개요 영역을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-130">The [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Query Editor generates outline regions for each element in the following hierarchy:</span></span>

1.  <span data-ttu-id="946dd-131">일괄 처리.</span><span class="sxs-lookup"><span data-stu-id="946dd-131">Batches.</span></span> <span data-ttu-id="946dd-132">첫 번째 일괄 처리는 파일의 시작 부분과 첫 번째 GO 명령 사이에 있는 코드입니다. GO 명령이 없는 경우에는 파일의 시작 부분과 파일의 끝 부분 사이에 있는 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-132">The first batch is the code from the start of the file to either the first GO command or the end of the file when there are no GO commands.</span></span> <span data-ttu-id="946dd-133">첫 번째 GO 다음에는 각 GO 명령과 다음 GO 명령 또는 파일의 끝 부분 사이에 하나의 일괄 처리가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-133">After the first GO, there is one batch from each GO command to either the next GO command or the end of the file.</span></span>

2.  <span data-ttu-id="946dd-134">다음 키워드로 구분된 블록</span><span class="sxs-lookup"><span data-stu-id="946dd-134">Blocks delimited by the following keywords:</span></span>

    -   <span data-ttu-id="946dd-135">BEGIN - END</span><span class="sxs-lookup"><span data-stu-id="946dd-135">BEGIN - END</span></span>

    -   <span data-ttu-id="946dd-136">BEGIN TRY - END TRY</span><span class="sxs-lookup"><span data-stu-id="946dd-136">BEGIN TRY - END TRY</span></span>

    -   <span data-ttu-id="946dd-137">BEGIN CATCH - END CATCH</span><span class="sxs-lookup"><span data-stu-id="946dd-137">BEGIN CATCH - END CATCH</span></span>

3.  <span data-ttu-id="946dd-138">여러 줄로 된 문</span><span class="sxs-lookup"><span data-stu-id="946dd-138">Multiline statements.</span></span>

 <span data-ttu-id="946dd-139">예를 들어 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 쿼리 편집기는 다음 쿼리에 대해 3개의 개요 영역을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-139">For example, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Query Editor creates three outline regions for the following query:</span></span>

```
CREATE PROCEDURE Sales.SampleProc --Outline region 1
AS
BEGIN --Outline region 2 
  SELECT GETDATE() AS TimeOfQuery;
  SELECT * --Outline region 3
  FROM sys.transmission_queue;
  SELECT @@VERSION;
END;
GO
```

 <span data-ttu-id="946dd-140">`SELECT *` 줄의 빼기 기호를 클릭하여 해당 `SELECT` 문만 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-140">You can click the minus sign on the `SELECT *` line to collapse just that `SELECT` statement.</span></span> <span data-ttu-id="946dd-141">전체 `BEGIN - END` 블록을 축소하려면 `BEGIN` 줄의 빼기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-141">To collapse the whole `BEGIN - END` block, click the minus sign on the `BEGIN` line.</span></span> <span data-ttu-id="946dd-142">전체 일괄 처리를 `GO` 명령으로 축소하려면 `CREATE PROCEDURE` 줄의 빼기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-142">To collapse the whole batch to the `GO` command, click the minus sign on the `CREATE PROCEDURE` line.</span></span> <span data-ttu-id="946dd-143">`SELECT GETDATE()` 또는 `SELECT @@VERSION` 줄은 한 줄로 된 문이고 개요 영역이 없기 때문에 개별적으로 축소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="946dd-143">You cannot collapse the `SELECT GETDATE()` or `SELECT @@VERSION` lines individually because they are single line statements and do not get outlining regions.</span></span>


