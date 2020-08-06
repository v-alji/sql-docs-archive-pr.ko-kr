---
title: 원본 테이블 및 뷰 선택(SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.selectsourcetablesandviews.f1
ms.assetid: f60e1a19-2ea6-403c-89ab-3e60ac533ea0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e18f9f34db7965033d4e1e62964060a26404a45e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652915"
---
# <a name="select-source-tables-and-views-sql-server-import-and-export-wizard"></a><span data-ttu-id="93107-102">원본 테이블 및 뷰 선택(SQL Server 가져오기 및 내보내기 마법사)</span><span class="sxs-lookup"><span data-stu-id="93107-102">Select Source Tables and Views (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="93107-103">**원본 테이블 및 뷰 선택** 페이지를 사용 하 여 데이터 원본에서 대상으로 복사할 테이블 및 뷰를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93107-103">Use the **Select Source Tables and Views** page to specify the tables and views to be copied from the data source to the destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93107-104">테이블 복사 옵션을 선택할 경우 테이블의 모든 열을 복사하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93107-104">You do not have to copy all the columns in a table when you select the Table Copy option.</span></span> <span data-ttu-id="93107-105">대상 테이블을 선택한 후 매핑 편집을 클릭 하 여 **열 매핑** 대화 상자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="93107-105">After selecting a destination table, click Edit Mappings to display the **Column Mappings** dialog box.</span></span> <span data-ttu-id="93107-106">**\<ignore>** 건너 뛰 려는 열에 대해 **열 매핑** 대화 상자의 **대상** 열에서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="93107-106">Select **\<ignore>** in the **Destination** column of the **Column Mappings** dialog box for columns that you want to skip.</span></span>  
  
 <span data-ttu-id="93107-107">이 마법사에 대해 자세히 알아보려면 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="93107-107">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="93107-108">마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="93107-108">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="93107-109">SQL Server 가져오기 및 내보내기 마법사의 목적은 원본에서 대상으로 데이터를 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="93107-109">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="93107-110">이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93107-110">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="93107-111">그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93107-111">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="93107-112">자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93107-112">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="93107-113">옵션</span><span class="sxs-lookup"><span data-stu-id="93107-113">Options</span></span>  
  
### <a name="tables-and-views-list"></a><span data-ttu-id="93107-114">테이블 및 뷰 목록</span><span class="sxs-lookup"><span data-stu-id="93107-114">Tables and views List</span></span>  
 <span data-ttu-id="93107-115">**원본**</span><span class="sxs-lookup"><span data-stu-id="93107-115">**Source**</span></span>  
 <span data-ttu-id="93107-116">사용 가능한 목록에서 확인란을 사용하여 대상으로 복사할 테이블 및 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="93107-116">Using the check boxes, select from the list of available tables and views to copy to the destination.</span></span> <span data-ttu-id="93107-117">원본 테이블 또는 뷰를 선택한 다음 다른 동작을 수행하지 않으면 원본 스키마 및 데이터가 변경되지 않고 대상으로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="93107-117">If you select a source table or view and perform no other action, the schema and data from the source are copied without changes.</span></span>  
  
 <span data-ttu-id="93107-118">**대상**</span><span class="sxs-lookup"><span data-stu-id="93107-118">**Destination**</span></span>  
 <span data-ttu-id="93107-119">목록에서 각 원본 테이블에 대한 대상 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="93107-119">Select a destination table from the list for each source table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93107-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]나 다른 도구를 사용하여 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 대상 테이블을 만들기 위해 마법사의 이 지점에서 일시 중지할 경우 사용 가능한 대상 테이블의 목록에 새 테이블이 즉시 표시되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93107-120">If you pause at this point in the wizard to create a destination table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or another tool, the new table is not immediately visible in the list of available destination tables.</span></span> <span data-ttu-id="93107-121">대상 테이블 목록을 새로 고치려면 두 페이지 뒤로 이동 하 여 **대상 선택** 페이지에서 대상 데이터베이스를 다시 선택한 다음 **원본 테이블 및 뷰를 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="93107-121">To refresh the list of destination tables, step back two pages to the **Choose a Destination** page, re-select the destination database, then step forward again to the **Select Source Tables and Views**.</span></span>  
  
### <a name="other-options"></a><span data-ttu-id="93107-122">다른 옵션</span><span class="sxs-lookup"><span data-stu-id="93107-122">Other Options</span></span>  
 <span data-ttu-id="93107-123">**매핑 편집**</span><span class="sxs-lookup"><span data-stu-id="93107-123">**Edit mappings**</span></span>  
 <span data-ttu-id="93107-124">**열 매핑** 대화 상자를 사용 하 여 원본 데이터를 받을 대상 열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93107-124">Use the **Column Mappings** dialog box to specify destination columns to receive the source data.</span></span> <span data-ttu-id="93107-125">\<ignore>건너 뛰 려는 열에 대해 **열 매핑** 대화 상자의 **대상** 열에서 선택 하 여 열의 하위 집합만 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93107-125">You can copy only a subset of columns by selecting \<ignore> in the **Destination** column of the **Column Mappings** dialog box for columns that you want to skip.</span></span>  
  
 <span data-ttu-id="93107-126">**미리 보기**</span><span class="sxs-lookup"><span data-stu-id="93107-126">**Preview**</span></span>  
 <span data-ttu-id="93107-127">**데이터 미리 보기** 대화 상자에서 원본 데이터를 미리 보고 가져오기 또는 내보내기 작업을 수행 하기 전에 데이터를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93107-127">Preview source data in the **Preview Data** dialog box to verify it before performing the import or export.</span></span> <span data-ttu-id="93107-128">**데이터 미리 보기** 대화 상자에는 최대 200 개의 데이터 행이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93107-128">The **Preview Data** dialog box displays up to 200 rows of data.</span></span>  
  
 <span data-ttu-id="93107-129">데이터를 미리 본 후 데이터 원본 및 대상에 대해 선택한 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93107-129">After previewing the data, you might want to change the options that you have selected for the data source and destination.</span></span> <span data-ttu-id="93107-130">이렇게 변경하려면 **원본 테이블 및 뷰 선택** 페이지에서 **뒤로** 를 클릭하여 선택 내용을 변경할 수 있는 이전 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="93107-130">To make these changes, on the **Select Source Tables and Views** page, click **Back** to return to previous pages where you can change your selections.</span></span>  
  
  
