---
title: 이름 일치 (데이터 원본 뷰 마법사) (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourceviewwizard.namematchingcriteria.f1
ms.assetid: 7f811e02-0fe6-45c9-a7b7-29c61032d96b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 50cc46db7f582e0aea1570dadc956336ef8be074
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651340"
---
# <a name="name-matching-data-source-view-wizard-analysis-services"></a><span data-ttu-id="1d7fa-102">이름 일치(데이터 원본 뷰 마법사)(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="1d7fa-102">Name Matching (Data Source View Wizard) (Analysis Services)</span></span>
  <span data-ttu-id="1d7fa-103">**이름 일치** 페이지를 사용하여 스키마의 데이터 원본 뷰에 대해 선택한 테이블과 해당 스키마의 다른 테이블 간의 관계를 감지하는 데 사용할 조건을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7fa-103">Use the **Name Matching** page to select the criterion to use for detecting possible relationships between the tables that you select for the data source view and the other tables in the schema.</span></span> <span data-ttu-id="1d7fa-104">테이블 간에 물리적 외래 키 관계가 없으면 이 기준이 관련 테이블을 식별하고 데이터 원본 뷰에 추가하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7fa-104">If no physical foreign key relationships exist between the tables, this criterion helps you identify and add related tables to the data source view.</span></span> <span data-ttu-id="1d7fa-105">이름 일치로 식별된 논리적 관계도 데이터 원본 뷰에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7fa-105">The logical relationships that are identified by name matching are also added to the data source view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d7fa-106">여러 테이블이 있지만 테이블 간에 외래 키 관계가 없는 데이터 원본을 선택하는 경우에만 이 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7fa-106">This page appears only if you select a data source that has multiple tables but no foreign key relationships between any one of the tables.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1d7fa-107">옵션</span><span class="sxs-lookup"><span data-stu-id="1d7fa-107">Options</span></span>  
 <span data-ttu-id="1d7fa-108">**일치하는 열을 기준으로 논리적 관계 만들기**</span><span class="sxs-lookup"><span data-stu-id="1d7fa-108">**Create logical relationships by matching columns**</span></span>  
 <span data-ttu-id="1d7fa-109">이름 일치 조건을 사용하여 스키마의 데이터 원본 뷰에 대해 선택한 테이블과 해당 스키마의 다른 테이블 간의 논리적 종속성 및 관계를 감지하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7fa-109">Select to use a name-matching criterion to detect possible logical dependencies and relationships between the tables that you select to include in the data source view and the other tables in the schema.</span></span> <span data-ttu-id="1d7fa-110">이 확인란 선택을 취소하면 데이터 원본의 테이블 간에 논리적 관계를 식별하는 데 이름 일치 조건을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7fa-110">If you clear this check box, no name-matching criterion is used to identify logical relationships between tables in the data source.</span></span>  
  
 <span data-ttu-id="1d7fa-111">**외래 키 일치**</span><span class="sxs-lookup"><span data-stu-id="1d7fa-111">**Foreign key matches**</span></span>  
 <span data-ttu-id="1d7fa-112">데이터 원본의 테이블과 뷰 간에 논리적 관계를 만드는 데 사용할 기준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7fa-112">Select the criterion to use for creating logical relationships between tables and views in the data source.</span></span> <span data-ttu-id="1d7fa-113">영숫자 이외의 문자는 일치 문자열에서 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7fa-113">Non-alphanumeric characters are ignored in matching strings.</span></span> <span data-ttu-id="1d7fa-114">예를 들어 "Customer ID", "Customer_ID", "CustomerID"는 모두 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7fa-114">For example, "Customer ID", "Customer_ID", "CustomerID" all match.</span></span> <span data-ttu-id="1d7fa-115">지정한 조건으로 관계를 만들려면 다음 표의 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7fa-115">Select one of the options in the following table to create relationships under the specified conditions.</span></span>  
  
|<span data-ttu-id="1d7fa-116">선택</span><span class="sxs-lookup"><span data-stu-id="1d7fa-116">Select</span></span>|<span data-ttu-id="1d7fa-117">만들 관계</span><span class="sxs-lookup"><span data-stu-id="1d7fa-117">To create</span></span>|  
|------------|---------------|  
|<span data-ttu-id="1d7fa-118">**기본 키와 같은 이름**</span><span class="sxs-lookup"><span data-stu-id="1d7fa-118">**Same name as primary key**</span></span>|<span data-ttu-id="1d7fa-119">열 이름이 선택한 테이블의 기본 키 열 이름과 같은 테이블에 대한 논리적 관계</span><span class="sxs-lookup"><span data-stu-id="1d7fa-119">A logical relationship to any table with a column name that matches the name of the primary key column in a selected table.</span></span>|  
|<span data-ttu-id="1d7fa-120">**대상 테이블 이름과 같은 이름**</span><span class="sxs-lookup"><span data-stu-id="1d7fa-120">**Same name as destination table name**</span></span>|<span data-ttu-id="1d7fa-121">열 이름이 선택한 테이블의 이름과 일치하는 테이블에 대한 논리적 관계</span><span class="sxs-lookup"><span data-stu-id="1d7fa-121">A logical relationship to any table with a column name that matches the name of a selected table.</span></span>|  
|<span data-ttu-id="1d7fa-122">**대상 테이블 이름 + 기본 키 이름**</span><span class="sxs-lookup"><span data-stu-id="1d7fa-122">**Destination table name + primary key name**</span></span>|<span data-ttu-id="1d7fa-123">열 이름이 선택한 테이블 이름과 선택한 테이블에 대한 기본 키 열 이름이 이 순서대로 연결되는 이름과 일치하는 테이블에 대한 논리적 관계.</span><span class="sxs-lookup"><span data-stu-id="1d7fa-123">A logical relationship to any table in which a column name matches the selected table name concatenated with the name of the primary key column for the selected table, in that order.</span></span> <span data-ttu-id="1d7fa-124">이 연결에서 영숫자 이외의 문자는 무시됩니다. 예를 들어 "Product ID", "Product_ID" 및 "ProductID"는 모두 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7fa-124">Non-alphanumeric characters within the concatenation are ignored (for example, "Product ID", "Product_ID" and "ProductID" all match).</span></span>|  
  
 <span data-ttu-id="1d7fa-125">**설명 및 샘플**</span><span class="sxs-lookup"><span data-stu-id="1d7fa-125">**Description and sample**</span></span>  
 <span data-ttu-id="1d7fa-126">선택한 조건에 대한 설명과 샘플을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7fa-126">View a description and a sample of the selected criterion.</span></span>  
  
  
