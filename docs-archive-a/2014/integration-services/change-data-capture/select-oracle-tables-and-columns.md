---
title: Oracle 테이블 및 열 선택 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- selTabCol
ms.assetid: bf73f80e-a954-4c5f-874e-17fdd4082715
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d51e597f1210643b1543ed981045ade7b2fc2b62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649125"
---
# <a name="select-oracle-tables-and-columns"></a><span data-ttu-id="e5b97-102">Oracle 테이블 및 열 선택</span><span class="sxs-lookup"><span data-stu-id="e5b97-102">Select Oracle Tables and Columns</span></span>
  <span data-ttu-id="e5b97-103">Oracle 테이블 및 열 선택 페이지를 사용하여 변경이 캡처되는 Oracle 원본 데이터베이스에서 테이블을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-103">Use the Select Oracle Tables and Columns page to select the tables from the Oracle source database where changes are captured.</span></span> <span data-ttu-id="e5b97-104">이 페이지는 다음과 같은 요소로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-104">This page has the following elements:</span></span>  
  
## <a name="options"></a><span data-ttu-id="e5b97-105">옵션</span><span class="sxs-lookup"><span data-stu-id="e5b97-105">Options</span></span>  
 <span data-ttu-id="e5b97-106">**테이블 목록**</span><span class="sxs-lookup"><span data-stu-id="e5b97-106">**Table list**</span></span>  
 <span data-ttu-id="e5b97-107">테이블 목록은 다음과 같은 세 개의 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-107">The table list has three columns:</span></span>  
  
-   <span data-ttu-id="e5b97-108">**Oracle 테이블 이름**: 테이블의 이름(테이블 스키마 포함)입니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-108">**Oracle Table Name**: The name of the table, including the table schema.</span></span>  
  
-   <span data-ttu-id="e5b97-109">**캡처 인스턴스**: 인스턴스별 변경 데이터 캡처 개체의 이름 지정에 사용되는 캡처 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-109">**Capture Instance**: The name of the capture instance used to name instance-specific change data capture objects.</span></span> <span data-ttu-id="e5b97-110">캡처 인스턴스는 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-110">The capture instance cannot be NULL.</span></span>  
  
     <span data-ttu-id="e5b97-111">지정하지 않으면 이름은 원본 스키마 이름에 원본 테이블 이름을 붙인 `<schema-name>_<table-name>`형식으로 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-111">If not specified, the name is derived from the source schema name plus the source table name in the format `<schema-name>_<table-name>`.</span></span> <span data-ttu-id="e5b97-112">캡처 인스턴스 이름은 100자를 초과할 수 없으며 데이터베이스 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-112">The capture instance name cannot exceed 100 characters and must be unique within the database.</span></span>  
  
     <span data-ttu-id="e5b97-113">이 열에서 셀을 클릭하여 **capture_instance**를 수동으로 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-113">You can click in any cell in this column to manually edit the **capture_instance**.</span></span>  
  
-   <span data-ttu-id="e5b97-114">**보안 역할**: 변경 데이터에 대한 액세스를 제어하는 데 사용되는 데이터베이스 제어 역할의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-114">**Security Role**: The name of the database gating role used to control access to change data.</span></span>  
  
     <span data-ttu-id="e5b97-115">이 열에서 셀을 클릭하여 **security_role**을 수동으로 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-115">You can click in any cell in this column to manually edit the **security_role**.</span></span>  
  
 <span data-ttu-id="e5b97-116">**테이블 추가**</span><span class="sxs-lookup"><span data-stu-id="e5b97-116">**Add Tables**</span></span>  
 <span data-ttu-id="e5b97-117">**테이블 추가** 를 클릭하면 테이블 선택 대화 상자가 열립니다. 이 대화 상자에서 [변경 내용을 캡처할 Oracle 테이블을 선택](select-oracle-tables-for-capturing-changes.md)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-117">Click **Add Tables** to open the Table Selection dialog box where you can [Select Oracle Tables for Capturing Changes](select-oracle-tables-for-capturing-changes.md).</span></span>  
  
 <span data-ttu-id="e5b97-118">**편집**</span><span class="sxs-lookup"><span data-stu-id="e5b97-118">**Edit**</span></span>  
 <span data-ttu-id="e5b97-119">목록에서 테이블을 선택하고 **편집** 을 선택하여 해당 테이블에 대한 **속성** 대화 상자를 엽니다. 이 대화 상자에서 [변경 캡처를 위해 선택된 테이블을 변경](make-changes-to-the-tables-selected-for-capturing-changes.md)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-119">Select a table from the list and select **Edit** to open the **Properties** dialog box for that table where you can [Make Changes to the Tables Selected for Capturing Changes](make-changes-to-the-tables-selected-for-capturing-changes.md).</span></span>  
  
 <span data-ttu-id="e5b97-120">**제거**</span><span class="sxs-lookup"><span data-stu-id="e5b97-120">**Remove**</span></span>  
 <span data-ttu-id="e5b97-121">목록에서 테이블을 선택하고 **제거** 를 클릭하여 CDC 인스턴스에서 테이블을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-121">Select a table from the list and click **Remove** to remove the table from the CDC instance.</span></span>  
  
 <span data-ttu-id="e5b97-122">올바른 대화 상자를 사용하여 [변경 내용을 캡처할 Oracle 테이블을 선택](select-oracle-tables-for-capturing-changes.md) 하고 [변경 캡처를 위해 선택된 테이블을 변경](make-changes-to-the-tables-selected-for-capturing-changes.md) 한 후에는 **다음** 을 클릭하여 [보완 로깅 스크립트를 생성 및 실행](generate-and-run-the-supplemental-logging-script.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e5b97-122">After you [Select Oracle Tables for Capturing Changes](select-oracle-tables-for-capturing-changes.md) and/or [Make Changes to the Tables Selected for Capturing Changes](make-changes-to-the-tables-selected-for-capturing-changes.md) using the correct dialog boxes, click **Next** to [Generate and Run the Supplemental Logging Script](generate-and-run-the-supplemental-logging-script.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b97-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5b97-123">See Also</span></span>  
 <span data-ttu-id="e5b97-124">[SQL Server 변경 데이터베이스 인스턴스를 만드는 방법](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="e5b97-124">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 <span data-ttu-id="e5b97-125">[테이블 편집](edit-tables.md) </span><span class="sxs-lookup"><span data-stu-id="e5b97-125">[Edit Tables](edit-tables.md) </span></span>  
 <span data-ttu-id="e5b97-126">[CDC 인스턴스에 테이블 추가](add-tables-to-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="e5b97-126">[Add Tables to a CDC Instance](add-tables-to-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="e5b97-127">테이블 속성 편집</span><span class="sxs-lookup"><span data-stu-id="e5b97-127">Edit the Table Properties</span></span>](edit-the-table-properties.md)  
  
  
