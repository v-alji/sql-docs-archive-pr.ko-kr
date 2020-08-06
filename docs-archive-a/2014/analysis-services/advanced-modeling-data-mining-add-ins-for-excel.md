---
title: 고급 모델링 (Excel 용 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: 042270a3-6ec7-4b52-b2ba-2adb6c4740d5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 771eb6111765b558995ee3b0eb98196c63951567
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648234"
---
# <a name="advanced-modeling-data-mining-add-ins-for-excel"></a><span data-ttu-id="23111-102">고급 모델링(Excel용 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="23111-102">Advanced Modeling (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="23111-103">**고급** 데이터 모델링 옵션을 사용 하 여 사용자 지정 데이터 마이닝 구조 및 모델을 만들 수 있습니다 .이 구조는 마법사에서 만든 매개 변수와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="23111-103">You can use the **Advanced** data modeling options to create custom data mining structures and models with parameters different from those created by the wizards.</span></span> <span data-ttu-id="23111-104">이 섹션에서 설명하는 두 가지 마법사를 사용하면 완전히 새로운 데이터 마이닝 구조 및 새로운 마이닝 모델을 만들어 기존 데이터 마이닝 구조에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23111-104">The two wizards described in this section help you create a completely new data mining structure, and a new mining model to apply to an existing data mining structure.</span></span>  
  
## <a name="create-mining-structure"></a><span data-ttu-id="23111-105">마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="23111-105">Create Mining Structure</span></span>  
 <span data-ttu-id="23111-106">![데이터 마이닝 리본, 마이닝 구조 만들기 단추](media/dmc-createstruct.gif "데이터 마이닝 리본, 마이닝 구조 만들기 단추")</span><span class="sxs-lookup"><span data-stu-id="23111-106">![Create Mining Structure button, Data Mining ribbon](media/dmc-createstruct.gif "Create Mining Structure button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="23111-107">**마이닝 구조 만들기 마법사** 를 사용 하 여 새 데이터 마이닝 구조를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23111-107">The **Create Mining Structure Wizard** helps you build a new data mining structure.</span></span> <span data-ttu-id="23111-108">구조는 지정된 데이터 원본에서 추출된 데이터의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="23111-108">A structure is a collection of data extracted from a specified data source.</span></span>  <span data-ttu-id="23111-109">원본의 새 데이터로 마이닝 구조를 업데이트할 수 있지만, 마이닝 구조를 만들 때 데이터가 분석에 사용되는 방법을 정의하는 데이터 형식과 이름을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="23111-109">A mining structure can be updated with new data at the source, but when you create the mining structure, you define data types and names that define how the data is used for analysis.</span></span>  
  
 <span data-ttu-id="23111-110">다음 데이터 원본을 사용 하 여 Excel 테이블, Excel 범위 또는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터 원본 뷰로 이미 정의 된 외부 데이터 원본의 데이터를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23111-110">You can use the following data sources to build your structure: an Excel table, an Excel range, or any data in an external data source that has already been defined as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source view.</span></span>  
  
 <span data-ttu-id="23111-111">각 구조에 대해 테스트 및 유효성 검사에 사용할 일부 데이터를 따로 설정하는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23111-111">For each structure, you have the option of setting aside some of the data to use for testing and validation.</span></span> <span data-ttu-id="23111-112">데이터 원본을 설정할 때이 *홀드 아웃 데이터 집합* 을 만들면 해당 구조를 기반으로 하는 모든 모델이 테스트를 위해 일관 된 데이터 집합을 사용할 수 있도록 보장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23111-112">By creating this *holdout data set* when you set up your data sources, you can ensure that all models that are based on the structure are able to use a consistent data set for testing.</span></span>  
  
 <span data-ttu-id="23111-113">마이닝 구조를 만든 후에는 여러 모델을 추가하여 서로 다른 분석 방법을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23111-113">After you have created a mining structure, you can add multiple models to apply different methods of analysis.</span></span>  
  
 <span data-ttu-id="23111-114">**마이닝 구조 만들기 마법사**를 사용 하는 방법에 대 한 자세한 내용은 [마이닝 구조 &#40;SQL Server 데이터 마이닝 추가 기능&#41;만들기 ](create-mining-structure-sql-server-data-mining-add-ins.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="23111-114">For more information about how to use the **Create Mining Structure Wizard**, see [Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="add-model-to-structure"></a><span data-ttu-id="23111-115">구조에 모델 추가</span><span class="sxs-lookup"><span data-stu-id="23111-115">Add Model to Structure</span></span>  
 <span data-ttu-id="23111-116">![구조에 모델 추가 단추](media/dmc-addmodel.gif "구조에 모델 추가 단추")</span><span class="sxs-lookup"><span data-stu-id="23111-116">![Add Model to Structure button](media/dmc-addmodel.gif "Add Model to Structure button")</span></span>  
  
 <span data-ttu-id="23111-117">구조에 새 모델을 추가할 때 다른 알고리즘 또는 다른 매개 변수를 사용하여 데이터를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="23111-117">When you add a new model to a structure, you analyze the data by using a different algorithm, or with different parameters.</span></span> <span data-ttu-id="23111-118">이 옵션은 데이터 마이닝 클라이언트 도구에서는 표시되지 않는 알고리즘 중 하나를 사용하여 모델을 만들려는 경우 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="23111-118">This option is particularly useful if you want to create a model using one of the algorithms not exposed in the Data Mining Client tools.</span></span>  
  
 <span data-ttu-id="23111-119">예를 들어, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 지원하는 다음과 같은 알고리즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23111-119">For example, you can use any of the algorithms supported by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], such as:</span></span>  
  
-   <span data-ttu-id="23111-120">선형 회귀</span><span class="sxs-lookup"><span data-stu-id="23111-120">Linear regression</span></span>  
  
-   <span data-ttu-id="23111-121">시퀀스 클러스터링</span><span class="sxs-lookup"><span data-stu-id="23111-121">Sequence clustering</span></span>  
  
-   <span data-ttu-id="23111-122">중첩된 데이터 집합에 대한 연결 분석</span><span class="sxs-lookup"><span data-stu-id="23111-122">Association analysis on nested data sets</span></span>  
  
 <span data-ttu-id="23111-123">사용할 수 있는 마이닝 구조의 종류를 확인 하려면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] **모델 관리** 또는 **찾아보기**를 클릭 하 여에 저장 된 모델 및 구조를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23111-123">To see what kind of mining structures are available, you can browse the models and structures stored in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] by clicking either **Manage Models** or **Browse**.</span></span>  
  
 <span data-ttu-id="23111-124">현재 세션 중 만든 데이터 마이닝 구조나 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 저장된 마이닝 구조로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="23111-124">You are limited to data mining structures that were created during the current session, or mining structures that were saved to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="23111-125">자세한 내용은 [Excel 용 데이터 마이닝 추가 기능 &#40;구조에 모델 추가&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="23111-125">For more information, see [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23111-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23111-126">See Also</span></span>  
 <span data-ttu-id="23111-127">[모델 관리 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](manage-models-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="23111-127">[Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="23111-128">Excel &#40;SQL Server 데이터 마이닝 추가 기능을 검색 하는 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="23111-128">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
