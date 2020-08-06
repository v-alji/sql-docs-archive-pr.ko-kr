---
title: 관계형 데이터 원본에서 가져오기 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
author: minewiskan
ms.author: owend
ms.openlocfilehash: 93bb9ba9ba8d40262e4e90e840dcd15ac6826df3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660189"
---
# <a name="import-from-a-relational-data-source-ssas-tabular"></a><span data-ttu-id="bc394-102">관계형 데이터 원본에서 가져오기(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="bc394-102">Import from a Relational Data Source (SSAS Tabular)</span></span>
  <span data-ttu-id="bc394-103">테이블 가져오기 마법사를 사용하여 다양한 관계형 데이터베이스에서 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-103">You can import data from a variety of relational databases by using the Table Import Wizard.</span></span> <span data-ttu-id="bc394-104">마법사는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]모델 **메뉴의** 에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-104">The wizard is available in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Model** menu.</span></span> <span data-ttu-id="bc394-105">데이터 원본에 연결하려면 컴퓨터에 적절한 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span> <span data-ttu-id="bc394-106">지원되는 데이터 원본 및 공급자에 대한 자세한 내용은 [지원되는 데이터 원본&#40;SSAS 테이블 형식&#41;](tabular-models/data-sources-supported-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bc394-106">For more information about supported data sources and providers, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="bc394-107">테이블 가져오기 마법사를 사용하면 다음과 같은 데이터 원본에서 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-107">The Table Import Wizard supports importing data from the following data sources:</span></span>  
  
 <span data-ttu-id="bc394-108">**관계형 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="bc394-108">**Relational Databases**</span></span>  
  
-   <span data-ttu-id="bc394-109">Microsoft SQL Server 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="bc394-109">Microsoft SQL Server database</span></span>  
  
-   <span data-ttu-id="bc394-110">Microsoft SQL Azure</span><span class="sxs-lookup"><span data-stu-id="bc394-110">Microsoft SQL Azure</span></span>  
  
-   <span data-ttu-id="bc394-111">Microsoft Access 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="bc394-111">Microsoft Access database</span></span>  
  
-   <span data-ttu-id="bc394-112">Microsoft SQL Server 병렬 데이터 웨어하우스</span><span class="sxs-lookup"><span data-stu-id="bc394-112">Microsoft SQL Server Parallel Data Warehouse</span></span>  
  
-   <span data-ttu-id="bc394-113">Oracle</span><span class="sxs-lookup"><span data-stu-id="bc394-113">Oracle</span></span>  
  
-   <span data-ttu-id="bc394-114">Teradata</span><span class="sxs-lookup"><span data-stu-id="bc394-114">Teradata</span></span>  
  
-   <span data-ttu-id="bc394-115">Sybase</span><span class="sxs-lookup"><span data-stu-id="bc394-115">Sybase</span></span>  
  
-   <span data-ttu-id="bc394-116">Informix</span><span class="sxs-lookup"><span data-stu-id="bc394-116">Informix</span></span>  
  
-   <span data-ttu-id="bc394-117">IBM DB2</span><span class="sxs-lookup"><span data-stu-id="bc394-117">IBM DB2</span></span>  
  
-   <span data-ttu-id="bc394-118">OLE DB/ODBC</span><span class="sxs-lookup"><span data-stu-id="bc394-118">OLE DB/ODBC</span></span>  
  
 <span data-ttu-id="bc394-119">**다차원 원본**</span><span class="sxs-lookup"><span data-stu-id="bc394-119">**Multidimensional Sources**</span></span>  
  
-   <span data-ttu-id="bc394-120">Microsoft SQL Server Analysis Services 큐브</span><span class="sxs-lookup"><span data-stu-id="bc394-120">Microsoft SQL Server Analysis Services cube</span></span>  
  
 <span data-ttu-id="bc394-121">테이블 가져오기 마법사에서는 데이터 원본이 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 통합 문서인 경우 데이터를 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-121">The Table Import Wizard does not support importing data from a [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Workbook as a data source.</span></span>  
  
### <a name="to-import-data-from-a-database"></a><span data-ttu-id="bc394-122">데이터베이스에서 데이터를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="bc394-122">To import data from a database</span></span>  
  
1.  <span data-ttu-id="bc394-123">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 **모델** 메뉴를 클릭한 다음 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="bc394-124">**데이터 원본에 연결** 페이지에서 연결할 데이터베이스의 유형을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-124">On the **Connect to a Data Source** page, select the type of database to connect to, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="bc394-125">테이블 가져오기 마법사의 단계별 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-125">Follow the steps in the Table Import Wizard.</span></span> <span data-ttu-id="bc394-126">마법사 단계에서 **테이블 및 뷰 선택** 페이지를 사용하거나 **SQL 쿼리 지정** 페이지에서 SQL 쿼리를 만들어 특정 테이블과 뷰를 선택하거나 필터를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc394-126">On subsequent pages, you will be able to select specific tables and views or apply filters by using the **Select Tables and Views** page or by creating a SQL query on **Specify a SQL Query** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc394-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc394-127">See Also</span></span>  
 <span data-ttu-id="bc394-128">[SSAS 테이블 형식&#41;&#40;데이터 가져오기](import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="bc394-128">[Import Data &#40;SSAS Tabular&#41;](import-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="bc394-129">지원되는 데이터 원본&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="bc394-129">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
