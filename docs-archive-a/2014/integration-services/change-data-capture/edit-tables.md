---
title: 테이블 편집 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- tabProps
ms.assetid: fed8fada-2abc-45e2-8228-0656f9c599cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8e8058a0c3e8b81814283f055e4c4ac2b08dd2fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646584"
---
# <a name="edit-tables"></a><span data-ttu-id="cb44c-102">테이블 편집</span><span class="sxs-lookup"><span data-stu-id="cb44c-102">Edit Tables</span></span>
  <span data-ttu-id="cb44c-103">**테이블** 탭을 사용하여 Oracle 원본 데이터베이스에서 선택한 테이블과 열을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-103">Use the **Tables** tab to make changes to the tables and columns that you selected from the Oracle source database.</span></span> <span data-ttu-id="cb44c-104">이 탭은 다음과 같은 요소로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-104">This tab has the following elements:</span></span>  
  
 <span data-ttu-id="cb44c-105">**테이블 목록**</span><span class="sxs-lookup"><span data-stu-id="cb44c-105">**Table list**</span></span>  
 <span data-ttu-id="cb44c-106">테이블 목록은 다음과 같은 세 개의 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-106">The table list has three columns:</span></span>  
  
-   <span data-ttu-id="cb44c-107">**Oracle 테이블 이름**: 테이블의 이름(테이블 스키마 포함)입니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-107">**Oracle Table Name**: The name of the table, including the table schema.</span></span>  
  
-   <span data-ttu-id="cb44c-108">**캡처 인스턴스**: 인스턴스별 변경 데이터 캡처 개체의 이름 지정에 사용되는 캡처 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-108">**Capture Instance**: The name of the capture instance used to name instance-specific change data capture objects.</span></span> <span data-ttu-id="cb44c-109">캡처 인스턴스는 NULL일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-109">The capture instance cannot be NULL.</span></span> <span data-ttu-id="cb44c-110">지정하지 않으면 이름은 원본 스키마 이름에 원본 테이블 이름을 붙인 `<schema-name>_<table-name>.` 형식으로 파생됩니다. 캡처 인스턴스 이름은 100자를 초과할 수 없으며 데이터베이스 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-110">If not specified, the name is derived from the source schema name plus the source table name in the format `<schema-name>_<table-name>.` The capture instance name cannot exceed 100 characters and must be unique within the database.</span></span> <span data-ttu-id="cb44c-111">이 열에서 셀을 클릭하여 **capture_instance**를 수동으로 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-111">You can click in any cell in this column to manually edit the **capture_instance**.</span></span>  
  
-   <span data-ttu-id="cb44c-112">**보안 역할**: 변경 데이터에 대한 액세스 권한을 얻는 데 사용되는 데이터베이스 역할의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-112">**Security Role**: The name of the database role used to gain access to change data.</span></span> <span data-ttu-id="cb44c-113">이 열에서 셀을 클릭하여 **security_role**을 수동으로 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-113">You can click in any cell in this column to manually edit the **security_role**.</span></span>  
  
 <span data-ttu-id="cb44c-114">**테이블 추가**</span><span class="sxs-lookup"><span data-stu-id="cb44c-114">**Add Tables**</span></span>  
 <span data-ttu-id="cb44c-115">**테이블 추가** 를 클릭하면 테이블 선택 대화 상자가 열립니다. 이 대화 상자에서 [CDC 인스턴스에 테이블을 추가](add-tables-to-a-cdc-instance.md)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-115">Click **Add Tables** to open the Table Selection dialog box where you can [Add Tables to a CDC Instance](add-tables-to-a-cdc-instance.md).</span></span> <span data-ttu-id="cb44c-116">이 세션에서 Oracle 데이터베이스에 처음으로 액세스하는 경우 [Connect to Oracle](connect-to-oracle.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-116">The first time this session that you access the Oracle database, you must [Connect to Oracle](connect-to-oracle.md).</span></span>  
  
 <span data-ttu-id="cb44c-117">**편집**</span><span class="sxs-lookup"><span data-stu-id="cb44c-117">**Edit**</span></span>  
 <span data-ttu-id="cb44c-118">목록에서 테이블을 선택하고 **편집** 을 선택하여 해당 테이블에 대한 **속성** 대화 상자를 엽니다. 이 대화 상자에서 [테이블 속성을 편집](edit-the-table-properties.md)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-118">Select a table from the list and select **Edit** to open the **Properties** dialog box for that table where you can [Edit the Table Properties](edit-the-table-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb44c-119">미러 테이블이 이미 있는 테이블에 대한 형식 매핑을 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-119">You cannot edit type mapping for tables that already have mirror tables.</span></span> <span data-ttu-id="cb44c-120">이 작업은 새 테이블에 대해서만 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-120">You can do this for new tables only.</span></span>  
  
 <span data-ttu-id="cb44c-121">**제거**</span><span class="sxs-lookup"><span data-stu-id="cb44c-121">**Remove**</span></span>  
 <span data-ttu-id="cb44c-122">목록에서 테이블을 선택하고 **제거** 를 클릭하여 CDC 인스턴스에서 테이블을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb44c-122">Select a table from the list and click **Remove** to remove the table from the CDC instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb44c-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb44c-123">See Also</span></span>  
 <span data-ttu-id="cb44c-124">[CDC 인스턴스 속성을 편집하는 방법](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="cb44c-124">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 [<span data-ttu-id="cb44c-125">Oracle 테이블 및 열 선택</span><span class="sxs-lookup"><span data-stu-id="cb44c-125">Select Oracle Tables and Columns</span></span>](select-oracle-tables-and-columns.md)  
  
  
