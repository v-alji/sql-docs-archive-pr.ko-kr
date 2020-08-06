---
title: 테이블 복사 또는 쿼리 지정(SQL Server 가져오기 및 내보내기 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.specifytablecopyorquery.f1
ms.assetid: 08aa7158-40e6-4ef3-84d3-1265a8ba194c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a3d1eafb57475ed6a0f9fb20894fcc9718d1f0c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652912"
---
# <a name="specify-table-copy-or-query-sql-server-import-and-export-wizard"></a><span data-ttu-id="8929a-102">테이블 복사 또는 쿼리 지정(SQL Server 가져오기 및 내보내기 마법사)</span><span class="sxs-lookup"><span data-stu-id="8929a-102">Specify Table Copy or Query (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="8929a-103">**테이블 복사 또는 쿼리 지정** 페이지를 사용 하 여 데이터를 복사 하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-103">Use the **Specify Table Copy or Query** page to specify how to copy data.</span></span> <span data-ttu-id="8929a-104">그래픽 인터페이스를 사용하여 복사할 기존 데이터베이스 개체를 선택하거나 Transact-SQL을 사용하여 복잡한 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-104">You can use a graphical interface to select the existing database objects you want to copy, or you can use Transact-SQL to create a more complex query.</span></span>  
  
 <span data-ttu-id="8929a-105">이 마법사에 대해 자세히 알아보려면 [SQL Server 가져오기 및 내보내기 마법사](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8929a-105">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="8929a-106">마법사 시작 옵션 및 마법사를 성공적으로 실행 하는 데 필요한 사용 권한에 대 한 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사 실행](start-the-sql-server-import-and-export-wizard.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8929a-106">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="8929a-107">SQL Server 가져오기 및 내보내기 마법사의 목적은 원본에서 대상으로 데이터를 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-107">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="8929a-108">이 마법사는 대상 데이터베이스 및 대상 테이블도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-108">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="8929a-109">그러나 여러 개의 데이터베이스 또는 테이블을 복사하거나 다른 종류의 데이터베이스 개체를 복사할 경우 대신 데이터베이스 복사 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-109">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="8929a-110">자세한 내용은 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8929a-110">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8929a-111">옵션</span><span class="sxs-lookup"><span data-stu-id="8929a-111">Options</span></span>  
 <span data-ttu-id="8929a-112">**하나 이상의 테이블 또는 뷰에서 데이터 복사**</span><span class="sxs-lookup"><span data-stu-id="8929a-112">**Copy data from one or more tables or views**</span></span>  
 <span data-ttu-id="8929a-113">**원본 테이블 및 뷰 선택** 대화 상자를 사용 하 여 선택한 원본 테이블과 뷰의 필드를 지정한 대상에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-113">Copy fields from selected source tables and views to the specified destination or destinations by using the **Select Source Tables and Views** dialog box.</span></span> <span data-ttu-id="8929a-114">레코드를 필터링하거나 순서를 지정하지 않고 원본의 모든 데이터를 복사하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-114">Use this option if you want to copy all data in the source without filtering or ordering records.</span></span>  
  
 <span data-ttu-id="8929a-115">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자를 사용하여 데이터 원본에 연결하면 **하나 이상의 테이블 또는 뷰에서 데이터 복사** 옵션을 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-115">When you use a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] data provider to connect to your data source, the **Copy data from one or more tables or views** option might not be available.</span></span> <span data-ttu-id="8929a-116">이 옵션은 ProviderDescriptors.xml 파일에 ProviderDescription 섹션이 있는 공급자에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-116">This option is available only for those providers that have a ProviderDescription section in the ProviderDescriptors.xml file.</span></span> <span data-ttu-id="8929a-117">각 ProviderDescription 섹션에는 해당 공급자에서 메타데이터를 검색하는 데 필요한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-117">Each ProviderDescription section contains the information that is required to retrieve metadata from the corresponding provider.</span></span> <span data-ttu-id="8929a-118">기본적으로 다음 공급자에 대해서만 ProviderDescriptors.xml 파일에 ProviderDescription 섹션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-118">By default, the ProviderDescriptors.xml file contains a ProviderDescription section for only the following providers:</span></span>  
  
-   <span data-ttu-id="8929a-119">System.Data.SqlClient</span><span class="sxs-lookup"><span data-stu-id="8929a-119">System.Data.SqlClient</span></span>  
  
-   <span data-ttu-id="8929a-120">System.Data.OracleClient</span><span class="sxs-lookup"><span data-stu-id="8929a-120">System.Data.OracleClient</span></span>  
  
-   <span data-ttu-id="8929a-121">System.Data.OleDb</span><span class="sxs-lookup"><span data-stu-id="8929a-121">System.Data.OleDb</span></span>  
  
-   <span data-ttu-id="8929a-122">System.Data.Odbc</span><span class="sxs-lookup"><span data-stu-id="8929a-122">System.Data.Odbc</span></span>  
  
 <span data-ttu-id="8929a-123">추가 공급자에 대해 **하나 이상의 테이블 또는 뷰에서 데이터 복사** 옵션을 사용할 수 있도록 하기 위해 제 3 자가 ProviderDescriptors.xml 파일에 자체 providerdescriptor 섹션을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-123">To make the **Copy data from one or more tables or views** option available for additional providers, third parties can add their own ProviderDescriptor sections to the ProviderDescriptors.xml file.</span></span> <span data-ttu-id="8929a-124">기본적으로이 파일은 다음 위치에 \<*drive*> 있습니다.: FILES\MICROSOFT SQL server\100\dts\providerdescriptors</span><span class="sxs-lookup"><span data-stu-id="8929a-124">By default, this file is in \<*drive*>:\Program Files\Microsoft SQL Server\100\DTS\ProviderDescriptors.</span></span> <span data-ttu-id="8929a-125">ProviderDescriptor 섹션에 대한 요구 사항을 검토하려면 기본적으로 ProviderDescriptors.xml 파일과 같은 폴더에 있는 ProviderDescriptors.xsd 스키마 파일을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8929a-125">To review the requirements for the ProviderDescriptor section, see the ProviderDescriptors.xsd schema file that is, by default, in the same folder as the ProviderDescriptors.xml file.</span></span>  
  
 <span data-ttu-id="8929a-126">**전송 데이터를 지정할 쿼리 작성**</span><span class="sxs-lookup"><span data-stu-id="8929a-126">**Write a query to specify the data to transfer**</span></span>  
 <span data-ttu-id="8929a-127">**원본 쿼리 지정** 대화 상자를 사용 하 여 행을 검색 하는 SQL 문을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-127">Build SQL statements to retrieve rows by using the **Provide a Source Query** dialog box.</span></span> <span data-ttu-id="8929a-128">복사 작업 중에 원본 데이터를 수정하거나 제한하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-128">Use this option if you want to modify or restrict the source data during the copy operation.</span></span> <span data-ttu-id="8929a-129">선택 조건에 일치하는 행만 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8929a-129">Only the rows matching the selection criteria are available for copying.</span></span>  
  
  
