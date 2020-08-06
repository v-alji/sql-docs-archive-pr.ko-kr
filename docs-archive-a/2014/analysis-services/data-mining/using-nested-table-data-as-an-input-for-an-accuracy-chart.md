---
title: 정확도 차트에 대 한 입력으로 중첩 테이블 데이터 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services], nested tables
- Mining Accuracy Chart [Analysis Services], input tables
- nested tables
- adding nested tables
ms.assetid: 162e0686-ada3-4dd3-9151-9589926e6613
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97d5bbd75d09b1a9e4276c4723ad6986dbabf9e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639086"
---
# <a name="using-nested-table-data-as-an-input-for-an-accuracy-chart"></a><span data-ttu-id="82efe-102">정확도 차트에 대한 입력으로 중첩 테이블 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="82efe-102">Using Nested Table Data as an Input for an Accuracy Chart</span></span>
  <span data-ttu-id="82efe-103">외부 데이터를 사용하여 마이닝 모델의 정확도를 테스트할 때 마이닝 모델에 중첩 테이블이 포함되어 있으면 외부 데이터에도 사례 테이블 및 연결된 중첩 테이블이 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-103">When you test the accuracy of a mining model by using external data, if the mining model contains nested tables, the external data must also contain a case table and an associated nested table.</span></span>  
  
 <span data-ttu-id="82efe-104">이 항목에서는 모델 테스트에 사용되는 중첩 테이블에 대한 작업을 수행하는 방법과 모델 및 외부 데이터의 중첩 테이블 및 사례 테이블을 매핑하는 방법과 중첩 테이블에 필터를 적용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-104">This topic describes how to work with nested tables used for model testing, how to map nested and case tables in the mode and in the external data, and how to apply a filter to a nested table.</span></span>  
  
 <span data-ttu-id="82efe-105">중첩 테이블에 대한 작업을 수행할 때 다음 팁에 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-105">When working with nested tables, keep in mind these tips:</span></span>  
  
-   <span data-ttu-id="82efe-106">**마이닝 모델 테스트 사례 사용** 또는 **마이닝 구조 테스트 사례 사용**옵션을 선택한 경우에는 사례 테이블이나 중첩 테이블을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-106">If you select the option **Use mining model test cases** or **Use mining structure test cases**, you do not need to specify a case table or nested table.</span></span> <span data-ttu-id="82efe-107">이 옵션을 사용하면 테스트 데이터의 정의가 마이닝 구조에 저장되므로 정확도 차트를 만들 때 테스트 데이터가 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-107">With those options, the definition of the test data is stored in the mining structure and the test data is automatically selected when you create the accuracy chart.</span></span>  
  
-   <span data-ttu-id="82efe-108">데이터 원본의 사례 테이블과 중첩 테이블 간에 관계가 이미 설정되어 있는 경우 마이닝 구조의 열이 입력 테이블에 있는 동일한 이름의 열에 자동으로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-108">If a relationship already exists between the case and nested table in the data source, the columns in the mining structure are automatically mapped to the columns that have the same name in the input table.</span></span>  
  
-   <span data-ttu-id="82efe-109">사례 테이블을 지정하기 전에는 중첩 테이블을 선택할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-109">You cannot select a nested table until you have specified the case table.</span></span> <span data-ttu-id="82efe-110">또한 마이닝 모델에서 사례 테이블 및 중첩 테이블 구조를 사용하기 전에는 중첩 테이블을 입력으로 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-110">Also, you cannot specify a nested table as an input unless the mining model also uses a case table and nested table structure.</span></span>  
  
### <a name="use-a-nested-table-as-input-to-an-accuracy-chart"></a><span data-ttu-id="82efe-111">정확도 차트에 대한 입력으로 중첩 테이블 사용</span><span class="sxs-lookup"><span data-stu-id="82efe-111">Use a nested table as input to an accuracy chart</span></span>  
  
1.  <span data-ttu-id="82efe-112">마이닝 구조를 두 번 클릭하여 데이터 마이닝 디자이너에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-112">Double-click the mining structure to open it in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="82efe-113">**마이닝 정확도 차트** 탭을 선택한 다음 **입력 선택** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-113">Select the **Mining Accuracy Chart** tab, and then select the **Input Selection** tab.</span></span>  
  
3.  <span data-ttu-id="82efe-114">**정확도 차트에 사용할 데이터 집합을 선택하십시오**에서 **다른 데이터 집합 지정**옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-114">In **Select data set to be used for accuracy chart**, select the option **Specify a different data set**.</span></span>  
  
4.  <span data-ttu-id="82efe-115">찾아보기 단추 **(...)** 를 클릭 하 여 현재 서버의 데이터 원본 뷰 목록에서 외부 데이터 집합을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-115">Click the browse button **(...)** to choose the external data set from a list of data source views on the current server.</span></span>  
  
5.  <span data-ttu-id="82efe-116">**사례 테이블 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-116">Click **Select Case Table**.</span></span> <span data-ttu-id="82efe-117">**테이블 선택** 대화 상자에서 사례 데이터가 포함된 데이터 원본 뷰의 테이블을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-117">In the **Select Table** dialog box, choose the table from the data source view that contains the case data, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="82efe-118">**중첩 테이블 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-118">Click **Select Nested Table**.</span></span> <span data-ttu-id="82efe-119">**테이블 선택** 대화 상자에서 중첩 데이터가 포함된 테이블을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-119">In the **Select Table** dialog box, select the table that contains the nested data, and then click **OK**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="82efe-120">중첩 테이블과 사례 테이블 간의 관계를 수정해야 하는 경우 **조인 수정** 을 클릭하여 **관계 만들기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="82efe-120">If you need to modify the relationship between the nested table and the case table, click **Modify Join** to open the **Create Relationship** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82efe-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82efe-121">See Also</span></span>  
 <span data-ttu-id="82efe-122">[모델 테스트 데이터 선택 및 매핑](choose-and-map-model-testing-data.md) </span><span class="sxs-lookup"><span data-stu-id="82efe-122">[Choose and Map Model Testing Data](choose-and-map-model-testing-data.md) </span></span>  
 [<span data-ttu-id="82efe-123">모델 테스트 데이터에 필터 적용</span><span class="sxs-lookup"><span data-stu-id="82efe-123">Apply Filters to Model Testing Data</span></span>](apply-filters-to-model-testing-data.md)  
  
  
