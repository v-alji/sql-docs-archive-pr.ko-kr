---
title: 데이터 원본 뷰에서 논리적 기본 키 정의 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- removing logical primary keys
- logical primary keys [SQL Server]
- deleting logical primary keys
- data source views [Analysis Services], logical primary keys
ms.assetid: 172bc267-c637-4caa-bf55-0ba198d30b1e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25092e5d754381c572dcdbfc03e5ee0f29c1df24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651384"
---
# <a name="define-logical-primary-keys-in-a-data-source-view-analysis-services"></a><span data-ttu-id="4cebe-102">데이터 원본 뷰에서 논리적 기본 키 정의(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="4cebe-102">Define Logical Primary Keys in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="4cebe-103">데이터 원본 뷰 마법사와 데이터 원본 뷰 디자이너는 기본 데이터베이스 테이블을 기반으로 데이터 원본 뷰에 추가되는 테이블의 기본 키를 자동으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-103">The Data Source View Wizard and Data Source View Designer automatically define a primary key for a table that is added to a data source view based on underlying database table.</span></span>  
  
 <span data-ttu-id="4cebe-104">하지만 때로는 데이터 원본 뷰에서 수동으로 기본 키를 정의해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-104">Occasionally, you may need to manually define a primary key in the data source view.</span></span> <span data-ttu-id="4cebe-105">예를 들어 성능 또는 디자인상의 이유로 데이터 원본의 테이블이 기본 키 열을 명시적으로 정의하지 않았을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-105">For example, for performance or design reasons, tables in a data source may not have explicitly defined primary key columns.</span></span> <span data-ttu-id="4cebe-106">명명된 쿼리 및 뷰에서 테이블의 기본 키 열을 생략할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-106">Named queries and views may also omit the primary key column for a table.</span></span> <span data-ttu-id="4cebe-107">테이블, 뷰 또는 명명된 쿼리에 물리적 기본 키가 정의되어 있지 않으면 데이터 원본 뷰 디자이너에서 테이블, 뷰 또는 명명된 쿼리에 대해 수동으로 논리적 기본 키를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-107">If a table, view, or named query does not have a physical primary key defined, you can manually define a logical primary key on the table, view or named query in Data Source View Designer.</span></span>  
  
## <a name="set-a-logical-primary-key"></a><span data-ttu-id="4cebe-108">논리적 기본 키 설정</span><span class="sxs-lookup"><span data-stu-id="4cebe-108">Set a Logical Primary Key</span></span>  
 <span data-ttu-id="4cebe-109">기본 키는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 테이블의 레코드를 고유하게 식별하고, 차원 테이블의 키 열을 식별하며, 테이블, 뷰 및 명명된 쿼리 간의 관계를 지원하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-109">Primary keys are required in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to uniquely identify records in a table, identify key columns in dimension tables and to support relationships between tables, views and named queries.</span></span> <span data-ttu-id="4cebe-110">이러한 관계는 기본 데이터 원본에서 데이터 및 메타데이터를 검색할 쿼리를 작성하고 고급 비즈니스 인텔리전스 기능을 이용하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-110">These relationships are used to construct queries for retrieving data and metadata from underlying data sources, and to take advantage of advanced business intelligence features.</span></span>  
  
 <span data-ttu-id="4cebe-111">명명된 계산을 포함하여 모든 열을 논리적 기본 키에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-111">Any column can be used for the logical primary key, including a named calculation.</span></span> <span data-ttu-id="4cebe-112">논리적 기본 키를 만들면 데이터 원본 뷰에서 UNIQUE 제약 조건이 생성되며 PRIMARY KEY 제약 조건으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-112">When you create a logical primary key, a unique constraint is created in the data source view and marked as a primary key constraint.</span></span> <span data-ttu-id="4cebe-113">선택한 테이블에 지정된 기존의 다른 논리적 기본 키는 모두 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-113">Any other existing logical primary key specified in the selected table is deleted.</span></span>  
  
1.  <span data-ttu-id="4cebe-114">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 논리적 기본 키를 설정할 데이터 원본 뷰가 포함된 프로젝트를 열거나 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-114">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you wish to set a logical primary key.</span></span>  
  
2.  <span data-ttu-id="4cebe-115">솔루션 탐색기에서 **데이터 원본 뷰** 폴더를 확장한 다음 해당 데이터 원본 뷰를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-115">In Solution Explorer, expand the **Data Source Views** folder, then double-click the data source view.</span></span>  
  
     <span data-ttu-id="4cebe-116">테이블이나 뷰를 찾으려면 **데이터 원본 뷰** 메뉴를 클릭하거나 **테이블**  또는 **다이어그램** 창의 열린 영역을 마우스 오른쪽 단추로 클릭하여 **테이블 찾기** 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-116">To locate a table or view, you can use the **Find Table** option by either clicking the **Data Source View**  menu or right-clicking in an open area of the **Tables** or **Diagram** panes.</span></span>  
  
3.  <span data-ttu-id="4cebe-117">**테이블** 또는 **다이어그램** 창에서 논리적 기본 키를 정의하는 데 사용할 열을 마우스 오른쪽 단추로 클릭한 다음 **논리적 기본 키 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-117">In either the **Tables** or the **Diagram** pane, right-click the column or columns that you want to use to define a logical primary key, and then click **Set Logical Primary Key**.</span></span>  
  
     <span data-ttu-id="4cebe-118">논리적 기본 키 설정을 위한 옵션은 기본 키가 없는 테이블에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-118">The option to set a logical primary key is available only for tables that do not have a primary key.</span></span>  
  
     <span data-ttu-id="4cebe-119">키를 설정하면 키 아이콘을 통해 기본 키 열이 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cebe-119">Notice that after you set the key, a key icon now identifies the primary key columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cebe-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4cebe-120">See Also</span></span>  
 <span data-ttu-id="4cebe-121">[다차원 모델의 데이터 원본 뷰](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="4cebe-121">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="4cebe-122">데이터 원본 뷰에서 명명된 계산 정의&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4cebe-122">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
