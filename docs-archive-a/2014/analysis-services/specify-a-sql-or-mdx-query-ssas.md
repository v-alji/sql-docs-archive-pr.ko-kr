---
title: SQL 또는 MDX 쿼리 지정 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.specsqlmdxquery.f1
ms.assetid: e4128221-3b46-48be-b0f1-d82477ce6782
author: minewiskan
ms.author: owend
ms.openlocfilehash: bce5e92aaed7a62311e989d6963e4fa5764028ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736850"
---
# <a name="specify-a-sql-or-mdx-query-ssas"></a><span data-ttu-id="78da1-102">SQL 또는 MDX 쿼리 지정(SSAS)</span><span class="sxs-lookup"><span data-stu-id="78da1-102">Specify a SQL or MDX Query (SSAS)</span></span>
  <span data-ttu-id="78da1-103">**테이블 가져오기 마법사** 의 이 페이지에서는 SQL 또는 MDX 쿼리를 사용하여 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78da1-103">This page of the **Table Import Wizard** enables you to import data by using a SQL or MDX query.</span></span> <span data-ttu-id="78da1-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="78da1-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="78da1-105">가져올 데이터를 쿼리를 통해 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78da1-105">The query can manipulate the data that is imported.</span></span> <span data-ttu-id="78da1-106">예를 들어 서로 다른 테이블의 데이터를 조인하거나 특정 조건에 맞는 행만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78da1-106">For example, you could join data from different tables or select only rows that meet certain criteria.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="78da1-107">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="78da1-107">UI element list</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="78da1-108">용어</span><span class="sxs-lookup"><span data-stu-id="78da1-108">Term</span></span>|<span data-ttu-id="78da1-109">정의</span><span class="sxs-lookup"><span data-stu-id="78da1-109">Definition</span></span>|  
|<span data-ttu-id="78da1-110">**쿼리 이름**</span><span class="sxs-lookup"><span data-stu-id="78da1-110">**Friendly Query Name**</span></span>|<span data-ttu-id="78da1-111">쿼리의 고유 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="78da1-111">Type a unique name for the query.</span></span> <span data-ttu-id="78da1-112">이 이름은 반드시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78da1-112">This is a required field.</span></span>|  
|<span data-ttu-id="78da1-113">**SQL 문**</span><span class="sxs-lookup"><span data-stu-id="78da1-113">**SQL Statement**</span></span>|<span data-ttu-id="78da1-114">SQL 문을 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="78da1-114">Type or paste a SQL statement.</span></span>|  
|<span data-ttu-id="78da1-115">**유효성 검사**</span><span class="sxs-lookup"><span data-stu-id="78da1-115">**Validate**</span></span>|<span data-ttu-id="78da1-116">SQL 문이 유효한지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="78da1-116">Determine if the SQL statement is valid.</span></span>|  
|<span data-ttu-id="78da1-117">**디자인**</span><span class="sxs-lookup"><span data-stu-id="78da1-117">**Design**</span></span>|<span data-ttu-id="78da1-118">쿼리 디자이너 대화 상자를 사용하여 SQL 문을 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="78da1-118">Design a SQL statement by using the query designer dialog box.</span></span> <span data-ttu-id="78da1-119">자세한 내용은 [관계형 쿼리 디자이너&#40;SSAS&#41;](relational-query-designer-ssas.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="78da1-119">For more information, see [Relational Query Designer &#40;SSAS&#41;](relational-query-designer-ssas.md).</span></span>|  
  
  
