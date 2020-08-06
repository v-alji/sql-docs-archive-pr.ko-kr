---
title: 새 관계형 마이닝 구조 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], relational
- mining structures [Analysis Services], creating
- relational mining models [Analysis Services]
ms.assetid: 55bac3bd-700e-4f91-bcc6-f3cd8c026da1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b41dd3ac2e6144011c1b3acde27c4b5829a1661
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647333"
---
# <a name="create-a-new-relational-mining-structure"></a><span data-ttu-id="689ab-102">새 관계형 마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="689ab-102">Create a New Relational Mining Structure</span></span>
  <span data-ttu-id="689ab-103">데이터 마이닝 마법사를 사용 하 여 관계형 데이터베이스 또는 기타 원본의 데이터를 사용 하 여 새 마이닝 구조를 만든 다음 구조와 모든 관련 모델을 데이터베이스에 저장할 수 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-103">Use the Data Mining Wizard to create a new mining structure, using data from a relational database or other source, and then save the structure and any related models to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
### <a name="to-create-a-relational-mining-structure"></a><span data-ttu-id="689ab-104">관계형 마이닝 구조를 만들려면</span><span class="sxs-lookup"><span data-stu-id="689ab-104">To create a relational mining structure</span></span>  
  
1.  <span data-ttu-id="689ab-105">솔루션 탐색기에서 **프로젝트의** 마이닝 구조 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 폴더를 마우스 오른쪽 단추로 클릭하고 **새 마이닝 구조**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-105">In Solution Explorer, right-click the **Mining Structures** folder in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, and then click **New Mining Structure**.</span></span>  
  
     <span data-ttu-id="689ab-106">데이터 마이닝 마법사가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-106">The Data Mining Wizard opens.</span></span>  
  
2.  <span data-ttu-id="689ab-107">**데이터 마이닝 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-107">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="689ab-108">**정의 방법 선택** 페이지에서 **기존 관계형 데이터베이스 또는 데이터 웨어하우스 사용**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-108">On the **Select the Definition Method** page, select **From existing relational database or data warehouse**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="689ab-109">**데이터 마이닝 기술 선택** 페이지에서 사용할 데이터 마이닝 알고리즘을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-109">On the **Select the Data Mining Technique** page, select the data mining algorithm that you want to use, and then click **Next**.</span></span>  
  
     <span data-ttu-id="689ab-110">데이터 마이닝 알고리즘에 대한 자세한 내용은 [데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;](data-mining-algorithms-analysis-services-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="689ab-110">For more information about data mining algorithms, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
5.  <span data-ttu-id="689ab-111">**데이터 원본 뷰 선택** 페이지의 **사용 가능한 데이터 원본 뷰**에서 사용할 데이터 원본 뷰를 클릭하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-111">On the **Select Data Source View** page, under **Available data source views**, click the data source view that you want to use, and then click **Next**.</span></span>  
  
     <span data-ttu-id="689ab-112">데이터 원본 뷰 만들기에 대한 자세한 내용은 [다차원 모델의 데이터 원본 뷰](../multidimensional-models/data-source-views-in-multidimensional-models.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="689ab-112">For more information about creating a data source view, see [Data Source Views in Multidimensional Models](../multidimensional-models/data-source-views-in-multidimensional-models.md).</span></span>  
  
6.  <span data-ttu-id="689ab-113">**테이블 유형 지정** 페이지의 **입력 테이블**에서 사례 테이블과 중첩 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-113">On the **Specify Table Types** page, under **Input tables**, select a case table and a nested table.</span></span>  
  
7.  <span data-ttu-id="689ab-114">**학습 데이터 지정** 페이지의 **마이닝 모델 구조**에서 키 열, 입력 열 및 예측 가능한 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-114">On the **Specify the Training Data** page, under **Mining model structure**, select the key, input, and predictable columns.</span></span>  
  
     <span data-ttu-id="689ab-115">예측 가능한 열을 선택한 후 **제안** 단추를 클릭하여 **관련 열 제안** 대화 상자를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-115">After you select the predictable column, you can click the **Suggest** button to open the **Suggest Related Columns** dialog box.</span></span> <span data-ttu-id="689ab-116">선택한 열이 마이닝 구조에 포함되도록 이 대화 상자에서 **확인** 을 클릭하여 제안된 열을 적용하거나 **입력** 열의 선택 내용을 변경한 후 **확인**을 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-116">You can accept the suggested columns by clicking **OK** in this dialog box to include the selected columns in the mining structure, or you can change the selections in the **Input** column first, and then click **OK**.</span></span> <span data-ttu-id="689ab-117">제안 사항을 무시하려면 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-117">To ignore the suggestions, click **Cancel**.</span></span>  
  
8.  <span data-ttu-id="689ab-118">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-118">Click **Next**.</span></span>  
  
9. <span data-ttu-id="689ab-119">**열 내용 및 데이터 형식 지정** 페이지의 **마이닝 모델 구조**에서 각 열의 내용 유형과 데이터 형식을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-119">On the **Specify Columns' Content and Data Type** page, under **Mining model structure**, you can adjust the content type and data type for each column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="689ab-120">**검색** 을 클릭하여 열에 포함된 데이터가 연속 데이터인지 비연속 데이터인지 자동으로 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-120">You can click **Detect** to automatically detect whether a column contains continuous or discrete data.</span></span> <span data-ttu-id="689ab-121">이 단추를 클릭하면 **내용 유형** 열과 **데이터 형식** 열에서 열 내용 유형과 열 데이터 형식이 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-121">After you click this button, the column content and data types will be updated in the **Content Type** and **Data Type** columns.</span></span> <span data-ttu-id="689ab-122">콘텐츠 형식 및 데이터 형식에 대한 자세한 내용은 [콘텐츠 형식&#40;데이터 마이닝&#41;](content-types-data-mining.md) 및 [데이터 형식&#40;데이터 마이닝&#41;](data-types-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="689ab-122">For more information about content types and data types, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md) and [Data Types &#40;Data Mining&#41;](data-types-data-mining.md).</span></span>  
  
10. <span data-ttu-id="689ab-123">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-123">Click **Next**.</span></span>  
  
11. <span data-ttu-id="689ab-124">**마법사 완료** 페이지에서 마이닝 구조의 이름과 생성될 관련 초기 마이닝 모델을 지정하고 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="689ab-124">On the **Completing the Wizard** page, provide a name for the mining structure and the related initial mining model that will be created, and then click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="689ab-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="689ab-125">See Also</span></span>  
 [<span data-ttu-id="689ab-126">마이닝 구조 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="689ab-126">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
