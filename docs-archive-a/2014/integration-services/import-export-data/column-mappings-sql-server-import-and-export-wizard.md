---
title: 열 매핑(SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.columnmapandtransform.f1
ms.assetid: eadc54a6-f936-4ffc-91d7-fbfd2bdcab93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7994de1292677421447d441c1ac5aeb2b6fbc618
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652936"
---
# <a name="column-mappings-sql-server-import-and-export-wizard"></a><span data-ttu-id="79948-102">열 매핑(SQL Server 가져오기 및 내보내기 마법사)</span><span class="sxs-lookup"><span data-stu-id="79948-102">Column Mappings (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="79948-103">**열 매핑** 대화 상자를 사용 하 여 변환 매개 변수를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79948-103">Use the **Column Mappings** dialog box to edit transformation parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="79948-104">테이블 복사 옵션을 선택할 경우 테이블의 모든 열을 복사하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79948-104">You do not have to copy all the columns in a table when you select the Table Copy option.</span></span> <span data-ttu-id="79948-105">**\<ignore>** 이 대화 상자의 **대상** 열에서 건너 뛰 려는 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-105">Select **\<ignore>** in the **Destination** column of this dialog box for columns that you want to skip.</span></span>  
  
 <span data-ttu-id="79948-106">이 마법사에 대해 자세히 알아보려면 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79948-106">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="79948-107">마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 사용 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="79948-107">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="79948-108">SQL Server 가져오기 및 내보내기 마법사의 목적은 원본에서 대상으로 데이터를 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="79948-108">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="79948-109">이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79948-109">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="79948-110">그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-110">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="79948-111">자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79948-111">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="79948-112">옵션</span><span class="sxs-lookup"><span data-stu-id="79948-112">Options</span></span>  
 <span data-ttu-id="79948-113">**원본**</span><span class="sxs-lookup"><span data-stu-id="79948-113">**Source**</span></span>  
 <span data-ttu-id="79948-114">선택한 원본 테이블, 뷰 또는 쿼리를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-114">Identifies the selected source table, view, or query.</span></span>  
  
 <span data-ttu-id="79948-115">**대상**</span><span class="sxs-lookup"><span data-stu-id="79948-115">**Destination**</span></span>  
 <span data-ttu-id="79948-116">선택한 대상 테이블, 뷰 또는 쿼리를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-116">Identifies the selected destination table, view, or query.</span></span>  
  
 <span data-ttu-id="79948-117">**대상 테이블/파일 만들기**</span><span class="sxs-lookup"><span data-stu-id="79948-117">**Create destination table/file**</span></span>  
 <span data-ttu-id="79948-118">대상 테이블이 없는 경우 이를 만들지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-118">Specify whether to create the destination table if it does not already exist.</span></span>  
  
 <span data-ttu-id="79948-119">**대상 테이블/파일의 행 삭제**</span><span class="sxs-lookup"><span data-stu-id="79948-119">**Delete rows in destination table/file**</span></span>  
 <span data-ttu-id="79948-120">새 데이터를 로드하기 전에 기존 테이블에서 데이터를 지울지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-120">Specify whether to clear the data from an existing table before loading new data.</span></span>  
  
 <span data-ttu-id="79948-121">**대상 테이블/파일에 행 추가**</span><span class="sxs-lookup"><span data-stu-id="79948-121">**Append rows to destination table/file**</span></span>  
 <span data-ttu-id="79948-122">기존 테이블에 이미 있는 데이터에 새 데이터를 추가할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-122">Specify whether to append the new data to the data already present in an existing table.</span></span>  
  
 <span data-ttu-id="79948-123">**SQL 편집**</span><span class="sxs-lookup"><span data-stu-id="79948-123">**Edit SQL**</span></span>  
 <span data-ttu-id="79948-124">**테이블 생성 SQL 문** 대화 상자에서 기본 문을 사용 하거나 용도에 맞게 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-124">Use the default statement in the **Create Table SQL Statement** dialog box, or modify it for your purposes.</span></span> <span data-ttu-id="79948-125">이 문을 수정하는 경우 테이블 매핑에서도 관련 내용을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-125">If you modify this statement, you must also make associated changes to table mapping.</span></span>  
  
 <span data-ttu-id="79948-126">**대상 테이블을 삭제하고 다시 만들기**</span><span class="sxs-lookup"><span data-stu-id="79948-126">**Drop and re-create destination table**</span></span>  
 <span data-ttu-id="79948-127">대상 테이블을 덮어쓰려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-127">Choose this option to overwrite the destination table.</span></span> <span data-ttu-id="79948-128">이 옵션은 마법사를 사용하여 대상 테이블을 만들 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79948-128">This option is only available when you use the wizard to create the destination table.</span></span> <span data-ttu-id="79948-129">마법사에서 만든 패키지를 저장한 다음 해당 패키지를 다시 실행하는 경우에만 대상 테이블이 삭제되고 다시 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="79948-129">The destination table is only dropped and re-created if you save the package that the wizard creates, and then run the package again.</span></span>  
  
 <span data-ttu-id="79948-130">**ID 삽입 가능**</span><span class="sxs-lookup"><span data-stu-id="79948-130">**Enable identity insert**</span></span>  
 <span data-ttu-id="79948-131">원본 데이터의 기존 ID 값을 대상 테이블의 ID 열에 삽입할 수 있게 하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-131">Choose this option to allow existing identity values in the source data to be inserted into an identity column in the destination table.</span></span> <span data-ttu-id="79948-132">기본적으로 대상 ID 열에는 이러한 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79948-132">By default, the destination identity column does not allow this.</span></span>  
  
 <span data-ttu-id="79948-133">**매핑**</span><span class="sxs-lookup"><span data-stu-id="79948-133">**Mappings**</span></span>  
 <span data-ttu-id="79948-134">데이터 원본의 각 열이 대상의 열에 매핑되는 방식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-134">Displays how each column in the data source maps to a column in the destination.</span></span>  
  
 <span data-ttu-id="79948-135">이 목록에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79948-135">This list has the following columns:</span></span>  
  
 <span data-ttu-id="79948-136">**원본**</span><span class="sxs-lookup"><span data-stu-id="79948-136">**Source**</span></span>  
 <span data-ttu-id="79948-137">변환 매개 변수를 설정할 수 있는 각 원본 열을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="79948-137">View each source column for which you can set transformation parameters.</span></span>  
  
 <span data-ttu-id="79948-138">**대상**</span><span class="sxs-lookup"><span data-stu-id="79948-138">**Destination**</span></span>  
 <span data-ttu-id="79948-139">복사 작업 중에 특정 열을 무시할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-139">Specify whether you want to ignore a column during the copy operation.</span></span> <span data-ttu-id="79948-140">**\<ignore>** 건너 뛰 려는 열에 대해이 열에서를 선택 하 여 열의 하위 집합만 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79948-140">You can copy only a subset of columns by selecting **\<ignore>** in this column for columns that you want to skip.</span></span> <span data-ttu-id="79948-141">열을 매핑하기 전에 매핑하지 않을 열은 모두 무시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-141">Before you map columns, you must ignore all columns that will not be mapped.</span></span>  
  
 <span data-ttu-id="79948-142">**형식**</span><span class="sxs-lookup"><span data-stu-id="79948-142">**Type**</span></span>  
 <span data-ttu-id="79948-143">열에 대한 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-143">Select a data type for the column.</span></span>  
  
 <span data-ttu-id="79948-144">**Null 허용**</span><span class="sxs-lookup"><span data-stu-id="79948-144">**Nullable**</span></span>  
 <span data-ttu-id="79948-145">열에 Null 값을 허용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-145">Specify whether a column will allow a null value.</span></span>  
  
 <span data-ttu-id="79948-146">**크기**</span><span class="sxs-lookup"><span data-stu-id="79948-146">**Size**</span></span>  
 <span data-ttu-id="79948-147">열의 문자 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-147">Specify the number of characters in the column.</span></span>  
  
 <span data-ttu-id="79948-148">**정밀도**</span><span class="sxs-lookup"><span data-stu-id="79948-148">**Precision**</span></span>  
 <span data-ttu-id="79948-149">표시된 데이터의 전체 자릿수(숫자의 자릿수)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-149">Specify the precision of displayed data, referring to the number of digits.</span></span>  
  
 <span data-ttu-id="79948-150">**크기 조정**</span><span class="sxs-lookup"><span data-stu-id="79948-150">**Scale**</span></span>  
 <span data-ttu-id="79948-151">표시된 데이터의 소수 자릿수(소수점 이하 자릿수)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="79948-151">Specify the scale of displayed data, referring to the number of decimal places.</span></span>  
  
  
