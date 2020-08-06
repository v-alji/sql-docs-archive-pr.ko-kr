---
title: 테이블 속성(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.tabledesigner
- vdt.designers.properties.Table
ms.assetid: cc392987-1aab-45f5-b5af-a26be53409bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: df4a0332ebc622b069c468e51c461b7cba20aa36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735776"
---
# <a name="table-properties-visual-database-tools"></a><span data-ttu-id="cda79-102">테이블 속성(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="cda79-102">Table Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="cda79-103">테이블 디자이너 내부를 마우스 오른쪽 단추로 클릭한 다음 속성을 선택하는 경우 속성 창에 이러한 속성이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-103">These properties appear in the Properties window when you right click in Table Designer and select Properties.</span></span> <span data-ttu-id="cda79-104">별도로 언급하지 않는 한 테이블을 선택할 때 속성 창에서 이러한 속성을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-104">Unless otherwise noted, you can edit these properties in the Properties window when the table is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cda79-105">테이블이 복제용으로 게시된 경우 Transact-SQL 문 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 또는 SMO(SQL Server 관리 개체)를 사용하여 스키마를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-105">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="cda79-106">테이블 디자이너 또는 데이터베이스 다이어그램 디자이너를 사용하여 스키마를 변경하면 테이블 삭제 및 재생성이 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-106">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="cda79-107">게시된 개체를 삭제할 수 없으므로 스키마가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-107">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="show-table-properties-in-table-designer"></a><span data-ttu-id="cda79-108">테이블 디자이너에서 테이블 속성 표시</span><span class="sxs-lookup"><span data-stu-id="cda79-108">Show Table Properties in Table Designer</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cda79-109">이 항목의 속성은 사전순 대신 범주별로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-109">The properties in this topic are ordered by category rather than alphabet.</span></span>  
  
 <span data-ttu-id="cda79-110">**ID 범주**</span><span class="sxs-lookup"><span data-stu-id="cda79-110">**Identity Category**</span></span>  
 <span data-ttu-id="cda79-111">확장하면 **이름**, **설명**및 **스키마**에 대한 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-111">Expands to show properties for **Name**, **Description**, and **Schema**.</span></span>  
  
 <span data-ttu-id="cda79-112">**이름**</span><span class="sxs-lookup"><span data-stu-id="cda79-112">**Name**</span></span>  
 <span data-ttu-id="cda79-113">테이블의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-113">Displays the name of the table.</span></span> <span data-ttu-id="cda79-114">이름을 편집하려면 입력란에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-114">To edit the name, type in the text box.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="cda79-115">기존의 쿼리, 뷰, 사용자 정의 함수, 저장 프로시저 또는 프로그램에서 해당 테이블을 참조하는 경우 테이블의 이름을 수정하면 이 개체들은 유효하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-115">If existing queries, views, user-defined functions, stored procedures, or programs refer to the table, the name modification will make these objects invalid.</span></span>  
  
 <span data-ttu-id="cda79-116">**데이터베이스 이름**</span><span class="sxs-lookup"><span data-stu-id="cda79-116">**Database Name**</span></span>  
 <span data-ttu-id="cda79-117">선택한 테이블의 데이터 원본 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-117">Shows the name of the data source of the selected table.</span></span>  
  
 <span data-ttu-id="cda79-118">**설명**</span><span class="sxs-lookup"><span data-stu-id="cda79-118">**Description**</span></span>  
 <span data-ttu-id="cda79-119">선택한 테이블에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-119">Shows a description of the selected table.</span></span> <span data-ttu-id="cda79-120">전체 설명을 보거나 편집하려면 설명을 클릭한 다음, 속성의 오른쪽에 있는 줄임표 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-120">To see the entire description, or to edit it, click the description and then click the ellipses **(...)** to the right of the property.</span></span>  
  
 <span data-ttu-id="cda79-121">**스키마**</span><span class="sxs-lookup"><span data-stu-id="cda79-121">**Schema**</span></span>  
 <span data-ttu-id="cda79-122">현재 테이블이 속해 있는 스키마의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-122">Shows the name of the schema to which this table belongs.</span></span> <span data-ttu-id="cda79-123">Microsoft SQL Server에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-123">(Applies only to Microsoft SQL Server.)</span></span>  
  
 <span data-ttu-id="cda79-124">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="cda79-124">**Server Name**</span></span>  
 <span data-ttu-id="cda79-125">데이터 원본의 서버 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-125">Shows the name of the server for the data source.</span></span>  
  
 <span data-ttu-id="cda79-126">**테이블 디자이너 범주**</span><span class="sxs-lookup"><span data-stu-id="cda79-126">**Table Designer Category**</span></span>  
 <span data-ttu-id="cda79-127">확장하면 **ID 열**, **인덱싱 가능**및 **복제됨**에 대한 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-127">Expands to show properties for **Identity Column**, **Is Indexable**, and **Is Replicated**.</span></span>  
  
 <span data-ttu-id="cda79-128">**ID 열**</span><span class="sxs-lookup"><span data-stu-id="cda79-128">**Identity Column**</span></span>  
 <span data-ttu-id="cda79-129">테이블의 ID 열로 사용되는 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-129">Shows the column used as the table's identity column.</span></span> <span data-ttu-id="cda79-130">ID 열을 변경하려면 드롭다운 목록에서 원하는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-130">To change the identity column, choose from the drop-down list.</span></span> <span data-ttu-id="cda79-131">이 목록에는 숫자 데이터 형식의 열만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-131">Only columns of a numeric data type will show in the list.</span></span>  
  
 <span data-ttu-id="cda79-132">**인덱싱 가능**</span><span class="sxs-lookup"><span data-stu-id="cda79-132">**Is Indexable**</span></span>  
 <span data-ttu-id="cda79-133">테이블을 인덱싱할 수 있는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-133">Shows whether the table can be indexed.</span></span> <span data-ttu-id="cda79-134">테이블을 인덱싱할 수 없는 경우 테이블 소유자가 아니거나 데이터 형식이 텍스트, ntext 또는 이미지인 열이 테이블에 포함되어 있기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-134">If the table is not indexable it may be because you are not the table owner or because the table contains columns with data types of text, ntext, or image.</span></span>  
  
 <span data-ttu-id="cda79-135">**복제됨**</span><span class="sxs-lookup"><span data-stu-id="cda79-135">**Is Replicated**</span></span>  
 <span data-ttu-id="cda79-136">테이블이 다른 위치에 복제되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-136">Shows whether the table is replicated in another location.</span></span>  
  
 <span data-ttu-id="cda79-137">**기본 데이터 공간 사양 범주**</span><span class="sxs-lookup"><span data-stu-id="cda79-137">**Regular Data Space Specification Category**</span></span>  
 <span data-ttu-id="cda79-138">확장하면 **(데이터 공간 형식)** , **파일 그룹 또는 파티션 구성표 이름**및 **파티션 열 목록**에 대한 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-138">Expands to show properties for **(Data Space Type)**, **Filegroup or Partition Scheme Name**, and **Partition Column List**.</span></span>  
  
 <span data-ttu-id="cda79-139">**(데이터 공간 형식)**</span><span class="sxs-lookup"><span data-stu-id="cda79-139">**(Data Space Type)**</span></span>  
 <span data-ttu-id="cda79-140">현재 테이블을 저장하는 데 파일 그룹을 사용했는지 분할 구성표를 사용했는지 여부를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-140">Shows whether this table is stored using a filegroup or partition scheme.</span></span>  
  
 <span data-ttu-id="cda79-141">**파일 그룹 또는 파티션 구성표 이름**</span><span class="sxs-lookup"><span data-stu-id="cda79-141">**Filegroup or Partition Scheme Name**</span></span>  
 <span data-ttu-id="cda79-142">파일 그룹 또는 분할 구성표의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-142">Shows the name of the filegroup or partition scheme.</span></span>  
  
 <span data-ttu-id="cda79-143">**파티션 열 목록**</span><span class="sxs-lookup"><span data-stu-id="cda79-143">**Partition Column List**</span></span>  
 <span data-ttu-id="cda79-144">**파티션 열 목록** 대화 상자에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-144">Provides access to the **Partition Column List** dialog box.</span></span>  
  
 <span data-ttu-id="cda79-145">**행 GUID 열**</span><span class="sxs-lookup"><span data-stu-id="cda79-145">**Row GUID Column**</span></span>  
 <span data-ttu-id="cda79-146">Microsoft SQL Server에서 테이블의 ROWGUID 열로 사용되는 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-146">Shows the column used by Microsoft SQL Server as the table's ROWGUID column.</span></span> <span data-ttu-id="cda79-147">ROWGUID 열을 변경하려면 드롭다운 목록에서 원하는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-147">To change the ROWGUID column, choose from the drop-down list.</span></span> <span data-ttu-id="cda79-148">SQL Server 7.0 이상에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-148">(Applies only to SQL Server 7.0 or higher.)</span></span>  
  
 <span data-ttu-id="cda79-149">**Text/Image 파일 그룹**</span><span class="sxs-lookup"><span data-stu-id="cda79-149">**Text/Image Filegroup**</span></span>  
 <span data-ttu-id="cda79-150">데이터 형식이 텍스트 또는 이미지인 열에 대한 파일 그룹을 선택하는 데 사용할 수 있는 드롭다운 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-150">Provides a drop-down list from which you can choose the filegroup for columns that have text or image data types.</span></span> <span data-ttu-id="cda79-151">분할 구성표를 사용하여 테이블을 저장한 경우 이 필드를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="cda79-151">If the table is stored using a partition scheme, leave this field blank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda79-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cda79-152">See Also</span></span>  
 [<span data-ttu-id="cda79-153">테이블 디자인&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="cda79-153">Design Tables &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
