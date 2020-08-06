---
title: 쿼리 디자인 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.designquery.f1
ms.assetid: 2dad800f-10a1-453c-8761-2935b9826d84
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9b56d99ec11b50ce53ef223a01eb5fc2766238ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735095"
---
# <a name="design-the-query"></a><span data-ttu-id="85566-102">쿼리 디자인</span><span class="sxs-lookup"><span data-stu-id="85566-102">Design the Query</span></span>
  <span data-ttu-id="85566-103">보고서 마법사의 쿼리 디자인 페이지를 사용하여 쿼리를 수동으로 입력하거나 쿼리 작성기에서 대화형으로 쿼리를 작성하거나 다른 보고서에서 쿼리를 가져오는 방법을 통해 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85566-103">Use this page of the Report Wizard to create a query by typing the query manually, by using Query Builder to interactively build a query, or by importing a query from another report.</span></span>  
  
 <span data-ttu-id="85566-104">보고서 마법사의 이전 페이지인 데이터 원본 선택 페이지에서 선택한 데이터 원본 유형에 따라 이 페이지에 입력할 수 있는 쿼리가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="85566-104">The data source type you chose on the Select the Data Source page, a previous page in the Report Wizard, determines the query you can enter on this page.</span></span> <span data-ttu-id="85566-105">예를 들어 데이터 원본 유형이 인 경우 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] 문이나 저장 프로시저 이름을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85566-105">For example, if the data source type is [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements or stored procedure names.</span></span> <span data-ttu-id="85566-106">데이터 원본 유형이 인 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 쿼리 창을 사용할 수 없으며 쿼리를 직접 입력할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85566-106">If the data source type is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], the Query pane is disabled and you cannot enter a query directly.</span></span> <span data-ttu-id="85566-107">쿼리 작성기를 사용하여 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85566-107">You can specify the query by using Query Builder.</span></span>  
  
## <a name="options"></a><span data-ttu-id="85566-108">옵션</span><span class="sxs-lookup"><span data-stu-id="85566-108">Options</span></span>  
 <span data-ttu-id="85566-109">**쿼리 문자열**</span><span class="sxs-lookup"><span data-stu-id="85566-109">**Query string**</span></span>  
 <span data-ttu-id="85566-110">보고서에 사용하려는 데이터를 검색할 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="85566-110">Type a query that retrieves the data you want to use in your report.</span></span>  
  
 <span data-ttu-id="85566-111">**쿼리 작성기**</span><span class="sxs-lookup"><span data-stu-id="85566-111">**Query Builder**</span></span>  
 <span data-ttu-id="85566-112">데이터 원본에 대한 쿼리 디자이너를 열거나 다른 보고서에서 쿼리를 가져오려면 **쿼리 작성기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="85566-112">Click **Query Builder** to open a query designer for the data source, or to import a query from another report.</span></span>  
  
 <span data-ttu-id="85566-113">쿼리 디자이너에 대한 자세한 내용은 [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="85566-113">For more information about query designers, see [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="85566-114">예제</span><span class="sxs-lookup"><span data-stu-id="85566-114">Example</span></span>  
 <span data-ttu-id="85566-115">데이터 원본 유형 **Microsoft SQL Server**의 경우 다음 쿼리는 데이터베이스 테이블에서 마지막 이름 목록을 검색 합니다 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] `Person` .</span><span class="sxs-lookup"><span data-stu-id="85566-115">For the data source type **Microsoft SQL Server**, the following query retrieves a list of last names from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database `Person` table.</span></span>  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 <span data-ttu-id="85566-116">데이터 원본 유형 **Microsoft SQL Server**의 경우 다음 쿼리는 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] `uspGetEmployeeManagers` id 번호가 1 인 직원에 대해 저장 프로시저를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="85566-116">For the data source type **Microsoft SQL Server**, the following query runs the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] stored procedure `uspGetEmployeeManagers` for the employee with identification number 1:</span></span>  
  
```  
EXEC uspgetEmployeeManagers '1';  
```  
  
## <a name="see-also"></a><span data-ttu-id="85566-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85566-117">See Also</span></span>  
 <span data-ttu-id="85566-118">[보고서 마법사 도움말](../../2014/reporting-services/report-wizard-help.md) </span><span class="sxs-lookup"><span data-stu-id="85566-118">[Report Wizard Help](../../2014/reporting-services/report-wizard-help.md) </span></span>  
 <span data-ttu-id="85566-119">[보고서 포함 된 데이터 집합 및 공유 데이터 집합 &#40;보고서 작성기 및 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="85566-119">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="85566-120">보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="85566-120">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-data/report-datasets-ssrs.md)  
  
  
