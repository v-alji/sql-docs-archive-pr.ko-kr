---
title: 다차원 데이터 원본에서 가져오기 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7f0793ea-a4c7-42e9-b722-2164a454ebca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b26cc8ed7237f87fa5e23c6a2fd47e18de2c165
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660741"
---
# <a name="import-from-a-multidimensional-data-source-ssas-tabular"></a><span data-ttu-id="0953a-102">다차원 데이터 원본에서 가져오기(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="0953a-102">Import from a Multidimensional Data Source (SSAS Tabular)</span></span>
  <span data-ttu-id="0953a-103">Analysis Services 큐브 데이터베이스를 테이블 형식 모델의 데이터 원본으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-103">You can use an Analysis Services cube database as a data source for a tabular model.</span></span> <span data-ttu-id="0953a-104">Analysis Services 큐브에서 데이터를 가져오려면 MDX 쿼리를 정의하여 가져올 데이터를 선택해야 합니다</span><span class="sxs-lookup"><span data-stu-id="0953a-104">In order to import data from an Analysis Services cube, you must define an MDX Query to select data to import.</span></span>  
  
 <span data-ttu-id="0953a-105">SQL Server Analysis Services 데이터베이스에 포함된 모든 데이터를 모델로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-105">Any data that is contained in a SQL Server Analysis Services database can be imported into a model.</span></span> <span data-ttu-id="0953a-106">차원의 일부 또는 전체를 추출하거나, 큐브에서 현재 연도의 매월 판매량 합계 등과 같은 집계 및 조각을 가져올 수 있습니다. 하지만 큐브에서 가져오는 모든 데이터는 일반 데이터여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-106">You can extract all or part of a dimension, or get slices and aggregates from the cube, such as the sum of sales, month by month, for the current year, etc. However, you should keep in mind all data that you import from a cube is flattened.</span></span> <span data-ttu-id="0953a-107">따라서 여러 차원을 따라 측정값을 검색하는 쿼리를 정의하는 경우 데이터를 가져올 때 각 차원이 별개의 열이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-107">Therefore, if you define a query that retrieves measures along multiple dimensions, the data will be imported with each dimension in a separate column.</span></span>  
  
 <span data-ttu-id="0953a-108">Analysis Services 큐브는 SQL Server 2005, SQL Server 2008, SQL Server 2008 R2, [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]또는 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]버전이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-108">Analysis Services cubes must be version SQL Server 2005, SQL Server 2008, SQL Server 2008 R2, [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], or [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
### <a name="to-import-data-from-an-analysis-services-cube"></a><span data-ttu-id="0953a-109">Analysis Services 큐브에서 데이터를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="0953a-109">To import data from an Analysis Services cube</span></span>  
  
1.  <span data-ttu-id="0953a-110">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 **모델** 메뉴를 클릭한 다음 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-110">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click the **Model** menu, and then click **Import from Data Source**.</span></span>  
  
2.  <span data-ttu-id="0953a-111">**데이터 원본에 연결** 페이지에서 **Microsoft Analysis Services**를 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-111">On the **Connect to a Data Source** page, select **Microsoft Analysis Services**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="0953a-112">테이블 가져오기 마법사의 단계별 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-112">Follow the steps in the Table Import Wizard.</span></span> <span data-ttu-id="0953a-113">**MDX 쿼리 지정** 페이지에서 MDX 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-113">You will be able to specify an MDX query on the **Specify a MDX Query** page.</span></span> <span data-ttu-id="0953a-114">MDX 쿼리 디자이너를 사용하려면 MDX 쿼리 지정 페이지에서 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0953a-114">To use the MDX Query Designer, on the Specify a MDX Query page, click **Design**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0953a-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0953a-115">See Also</span></span>  
 <span data-ttu-id="0953a-116">[SSAS 테이블 형식&#41;&#40;데이터 가져오기](import-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="0953a-116">[Import Data &#40;SSAS Tabular&#41;](import-data-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="0953a-117">지원되는 데이터 원본&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="0953a-117">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
