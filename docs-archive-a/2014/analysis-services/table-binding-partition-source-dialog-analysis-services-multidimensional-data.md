---
title: 테이블 바인딩 세부 정보 (파티션 원본 대화 상자) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitiontableselection.f1
ms.assetid: 67d05389-81ae-4a6b-947b-986d37ec72b1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10845e18a2b7c74a8ed3aeec42f710b9706dc94a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649715"
---
# <a name="table-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="b3466-102">테이블 바인딩 세부 정보(파티션 원본 대화 상자)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="b3466-102">Table Binding Detail (Partition Source Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="b3466-103">**파티션 원본** 대화 상자의 **테이블 바인딩** 옵션을 사용하여 파티션에 대한 데이터를 제공하는 팩트 테이블을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3466-103">Use the **Table Binding** option in the **Partition Source** dialog box to specify the fact table that provides the data for the partition.</span></span> <span data-ttu-id="b3466-104">**파티션 원본** 대화 상자의 **바인딩 유형** 옵션에서 **테이블 바인딩** 을 선택하여 이 창을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3466-104">You can display this pane by selecting **Table Binding** from the **Binding type** option in the **Partition Source** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b3466-105">옵션</span><span class="sxs-lookup"><span data-stu-id="b3466-105">Options</span></span>  
 <span data-ttu-id="b3466-106">**측정값 그룹**</span><span class="sxs-lookup"><span data-stu-id="b3466-106">**Measure group**</span></span>  
 <span data-ttu-id="b3466-107">이 파티션에 대한 측정값 그룹을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b3466-107">Displays the measure group for this partition.</span></span>  
  
 <span data-ttu-id="b3466-108">**찾는 위치**</span><span class="sxs-lookup"><span data-stu-id="b3466-108">**Look in**</span></span>  
 <span data-ttu-id="b3466-109">이 파티션의 원본 테이블이 들어 있는 데이터 원본 또는 데이터 원본 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3466-109">Select the data source or data source view that contains the source tables for this partition.</span></span> <span data-ttu-id="b3466-110">선택한 측정값 그룹에 사용되는 데이터 원본 뷰가 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3466-110">The data source view used by the selected measure group is selected by default.</span></span>  
  
 <span data-ttu-id="b3466-111">**테이블 필터**</span><span class="sxs-lookup"><span data-stu-id="b3466-111">**Filter tables**</span></span>  
 <span data-ttu-id="b3466-112">**사용 가능한 테이블**에 표시되는 테이블의 이름을 제한하는 데 사용할 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b3466-112">Type the string used to restrict, by table name, the tables displayed in **Available tables**.</span></span>  
  
 <span data-ttu-id="b3466-113">**테이블 찾기**</span><span class="sxs-lookup"><span data-stu-id="b3466-113">**Find tables**</span></span>  
 <span data-ttu-id="b3466-114">**사용 가능한 테이블**의 테이블 목록을 새로 고치고 **테이블 필터**에 문자열이 지정된 경우 목록을 추가로 제한하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3466-114">Select to refresh the list of tables in **Available tables**, further restricting the list if a string was specified in **Filter tables**.</span></span>  
  
 <span data-ttu-id="b3466-115">**사용 가능한 테이블**</span><span class="sxs-lookup"><span data-stu-id="b3466-115">**Available tables**</span></span>  
 <span data-ttu-id="b3466-116">파티션에 대한 원본 테이블로 사용할 테이블을 선택하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3466-116">Click to select the table to use as a source table for the partition.</span></span>  
  
 <span data-ttu-id="b3466-117">**테이블 필터**에서 필터를 지정하지 않은 경우 **측정값 그룹** 에서 지정한 측정값 그룹에 사용되는 팩트 테이블과 구조적으로 유사한 **찾는 위치** 에서 지정한 데이터 원본 또는 데이터 원본 뷰의 모든 테이블이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3466-117">If no filter is specified in **Filter tables**, all tables in the data source or data source view specified in **Look in** that are similar in structure to the fact table used by the measure group specified in **Measure group** are listed.</span></span>  
  
 <span data-ttu-id="b3466-118">**테이블 필터**에서 필터를 지정한 경우 앞의 조건을 만족하는 테이블 이름과 해당 필터를 비교하여 목록을 더 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="b3466-118">If a filter is specified in **Filter tables**, the list is further restricted by comparing the filter against the table names that meet the above criteria.</span></span> <span data-ttu-id="b3466-119">**테이블 필터** 에 지정한 문자열을 포함하고 있는 테이블만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3466-119">Only those tables that contain the string specified in **Filter tables** are displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3466-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b3466-120">See Also</span></span>  
 [<span data-ttu-id="b3466-121">파티션 원본 대화 상자 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="b3466-121">Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  
