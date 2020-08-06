---
title: 예측 쿼리 결과 보기 및 저장 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- prediction queries [Analysis Services]
- viewing prediction query results
- displaying prediction query results
- Mining Model Prediction [Analysis Services], viewing results
ms.assetid: abba4d24-3619-44c1-8279-88f27ad627d3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6da4b515c4280969f665dba2cf5bee5281df0a00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649817"
---
# <a name="view-and-save-the-results-of-a-prediction-query"></a><span data-ttu-id="1f080-102">예측 쿼리 결과 보기 및 저장</span><span class="sxs-lookup"><span data-stu-id="1f080-102">View and Save the Results of a Prediction Query</span></span>
  <span data-ttu-id="1f080-103">예측 쿼리 작성기를 사용 하 여에서 쿼리를 정의한 후 쿼리를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 실행 하 고 쿼리 결과 보기로 전환 하 여 결과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-103">After you have defined a query in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by using Prediction Query Builder, you can run the query and view the results by switching to the query result view.</span></span>  
  
 <span data-ttu-id="1f080-104">프로젝트에 정의 된 모든 데이터 원본의 테이블에 예측 쿼리 결과를 저장할 수 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1f080-104">You can save the results of a prediction query to a table in any data source that is defined in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="1f080-105">새 테이블을 만들거나 기존 테이블에 쿼리 결과를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-105">You can either create a new table or save the query results to an existing table.</span></span> <span data-ttu-id="1f080-106">기존 테이블에 결과를 저장할 경우 테이블에 현재 저장되어 있는 데이터를 덮어쓰도록 선택할 수 있습니다. 덮어쓰도록 선택하지 않으면 테이블의 기존 데이터에 쿼리 결과가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-106">If you save the results to an existing table, you can choose to overwrite the data that is currently stored in the table; otherwise, the query results are appended to the existing data in the table.</span></span>  
  
### <a name="run-a-query-and-view-the-results"></a><span data-ttu-id="1f080-107">쿼리 실행 및 결과 확인</span><span class="sxs-lookup"><span data-stu-id="1f080-107">Run a query and view the results</span></span>  
  
1.  <span data-ttu-id="1f080-108">**의 데이터 마이닝 디자이너에 있는** 마이닝 모델 예측 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]탭의 도구 모음에서 **결과** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-108">On the toolbar of the **Mining Model Prediction** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **Result** .</span></span>  
  
     <span data-ttu-id="1f080-109">쿼리 결과 보기가 열리고 쿼리가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-109">The query results view opens and runs the query.</span></span> <span data-ttu-id="1f080-110">쿼리 결과가 뷰어에 표로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-110">The results are displayed in a grid in the viewer.</span></span>  
  
### <a name="save-the-results-of-a-prediction-query-to-a-table"></a><span data-ttu-id="1f080-111">테이블에 예측 쿼리 결과 저장</span><span class="sxs-lookup"><span data-stu-id="1f080-111">Save the results of a prediction query to a table</span></span>  
  
1.  <span data-ttu-id="1f080-112">데이터 마이닝 디자이너에 있는 **마이닝 모델 예측** 탭의 도구 모음에서 **쿼리 결과 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-112">On the toolbar of the **Mining Model Prediction** tab in Data Mining Designer, click **Save query result**.</span></span>  
  
     <span data-ttu-id="1f080-113">**데이터 마이닝 쿼리 결과 저장** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-113">The **Save Data Mining Query Result** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="1f080-114">**데이터 원본** 목록에서 데이터 원본을 선택하거나 **새로 만들기** 를 클릭하여 새 데이터 원본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-114">Select a data source from the **Data Source** list, or click **New** to create a new data source.</span></span>  
  
3.  <span data-ttu-id="1f080-115">**테이블 이름** 입력란에 테이블 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-115">In the **Table Name** box, enter the name of the table.</span></span> <span data-ttu-id="1f080-116">이미 테이블이 있을 경우 테이블 내용을 쿼리 결과로 바꾸려면 **기존 항목 덮어쓰기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-116">If the table already exists, select **Overwrite if exists** to replace the contents of the table with the query results.</span></span> <span data-ttu-id="1f080-117">테이블 내용을 덮어쓰지 않으려면 이 확인란을 선택하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="1f080-117">If you do not want to overwrite the contents of the table, do not select this check box.</span></span> <span data-ttu-id="1f080-118">그러면 테이블의 기존 데이터에 새 쿼리 결과가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-118">The new query results will be appended to the existing data in the table.</span></span>  
  
4.  <span data-ttu-id="1f080-119">데이터 원본 뷰에 테이블을 추가하려면 **DSV에 추가** 에서 데이터 원본 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-119">Select a data source view from **Add to DSV** if you want to add the table to a data source view.</span></span>  
  
5.  <span data-ttu-id="1f080-120">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-120">Click **Save**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="1f080-121">대상이 계층적 행 집합을 지원하지 않는 경우 FALTTENED 키워드를 결과에 추가하여 플랫 테이블로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f080-121">If the destination does not support hierarchical rowsets, you can add the FALTTENED keyword to the results to save as a flat table.</span></span>  
  
  
