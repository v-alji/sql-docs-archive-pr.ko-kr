---
title: DirectQuery에 대 한 기본 연결 방법 설정 또는 변경 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f10d5678-d678-4251-8cce-4e30cfe15751
author: minewiskan
ms.author: owend
ms.openlocfilehash: 239c80ace0daa3498c8dafd8fea358ce540931d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736904"
---
# <a name="set-or-change-the-preferred-connection-method-for-directquery"></a><span data-ttu-id="57a86-102">DirectQuery의 기본 연결 방법 설정 또는 변경</span><span class="sxs-lookup"><span data-stu-id="57a86-102">Set or Change the Preferred Connection Method for DirectQuery</span></span>
  <span data-ttu-id="57a86-103">DirectQuery 모드에서 사용할 모델을 만들 때는 먼저 디자인 환경에서 DirectQuery 사용을 지원하도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-103">When you create a model for use in DirectQuery mode, you must first configure the design environment to support use of DirectQuery.</span></span> <span data-ttu-id="57a86-104">이렇게 하려면 [SSAS 테이블 형식&#41;&#40;DirectQuery 디자인 모드 사용 ](tabular-models/enable-directquery-mode-in-ssdt.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="57a86-104">To do this, see [Enable DirectQuery Design Mode &#40;SSAS Tabular&#41;](tabular-models/enable-directquery-mode-in-ssdt.md).</span></span>  
  
 <span data-ttu-id="57a86-105">모델을 배포할 준비가 되면 사용자가 DirectQuery 모드 중 하나를 사용하여 모델에 액세스할 수 있도록 다음과 같이 몇 가지 추가 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-105">When you are ready to deploy the model, you must set some additional properties to enable users to access your model using one of the DirectQuery modes:</span></span>  
  
-   <span data-ttu-id="57a86-106">모델에 대한 쿼리에서 캐시된 데이터를 사용할지 아니면 관계형 데이터 원본을 사용할지를 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-106">You must indicate whether queries against the model should use cached data or the relational data source.</span></span> <span data-ttu-id="57a86-107">혼합 모드 또는 DirectQuery 전용을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-107">You can use a hybrid mode or DirectQuery only.</span></span>  
  
-   <span data-ttu-id="57a86-108">파티션을 사용하는 경우 DirectQuery 데이터 원본으로 사용할 파티션을 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-108">If you are using partitions, you must indicate which partition to use as the DirectQuery data source.</span></span>  
  
-   <span data-ttu-id="57a86-109">SQL Server 데이터 원본에 액세스할 사용자를 위한 가장 옵션을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-109">You must set impersonation options for users who will be accessing the SQL Server data source.</span></span>  
  
 <span data-ttu-id="57a86-110">이 절차에서는 디자이너에서 DirectQuery 모델의 기본 연결 방법을 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-110">This procedure describes how to set the preferred connection method for a DirectQuery model in the designer.</span></span> <span data-ttu-id="57a86-111">또한 모델을 배포한 후 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 에서 이 속성을 변경하는 방법도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-111">It also describes how you can change this property in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] after the model has been deployed.</span></span>  
  
### <a name="to-set-the-preferred-connection-method-for-a-directquery-model"></a><span data-ttu-id="57a86-112">DirectQuery 모델의 기본 연결 방법을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="57a86-112">To set the preferred connection method for a DirectQuery model</span></span>  
  
1.  <span data-ttu-id="57a86-113">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 DirectQuery 모델의 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-113">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution file for the DirectQuery model.</span></span>  
  
2.  <span data-ttu-id="57a86-114">Visual Studio의 **프로젝트** 메뉴에서 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-114">In Visual Studio, from the **Project** menu, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="57a86-115">**속성** 창에서 **DirectQueryMode**속성을 다음과 같이 DirectQuery 사용을 지원하는 값 중 하나로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-115">In the **Properties** pane, change the property, **DirectQueryMode**, to one of the values that support DirectQuery usage:</span></span>  
  
    -   <span data-ttu-id="57a86-116">**InMemory with DirectQuery**: 이 옵션을 사용하면 모델이 배포되지만 모델에 대해 쿼리를 실행하기 전에 캐시를 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-116">**InMemory with DirectQuery**: If you use this option, the model is deployed but you must process the cache before you can run queries against the model.</span></span>  
  
    -   <span data-ttu-id="57a86-117">**DirectQuery with InMemory**: 이 옵션을 사용하면 캐시가 이미 처리된 경우 클라이언트에서 캐시를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-117">**DirectQuery with InMemory**: If you use this option, the cache will be available for use by clients if it has already been processed.</span></span> <span data-ttu-id="57a86-118">이 설정으로 모델을 배포하고 캐시를 처리하지 않으면 일부 클라이언트에서 모델에 연결하려고 할 때 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-118">If you deploy the model with this setting and do not process the cache, some clients must get an error on trying to connect to the model.</span></span>  
  
    -   <span data-ttu-id="57a86-119">**DirectQuery only**: 이 옵션을 사용하면 메타데이터가 배포되지만 모델에는 데이터가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-119">**DirectQuery only**: If you use this option, the metadata is deployed but the model has no data in it.</span></span> <span data-ttu-id="57a86-120">클라이언트에서 InMemory 모드를 사용하여 연결하려고 하면 모델이 없거나 처리되지 않았다는 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-120">Clients that attempt to connect using In-Memory mode will get an error, indicating that the model does not exist or has not been processed.</span></span>  
  
4.  <span data-ttu-id="57a86-121">오류가 발생하면 Visual Studio에서 **오류 목록** 을 열고 DirectQuery 모드에서 모델을 배포할 수 없도록 하는 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-121">If there are errors, in Visual Studio, open the **Error List** and resolve any problems that would prevent the model from being deployed in DirectQuery mode.</span></span>  
  
### <a name="to-verify-or-change-the-preferred-connection-method-for-a-directquery-model"></a><span data-ttu-id="57a86-122">DirectQuery 모델의 기본 연결 방법을 확인하거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="57a86-122">To verify or change the preferred connection method for a DirectQuery model</span></span>  
  
1.  <span data-ttu-id="57a86-123">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]에서 DirectQuery 모델을 배포한 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-123">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to the instance where you deployed the DirectQuery model.</span></span>  
  
2.  <span data-ttu-id="57a86-124">model 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-124">Right-click the model database, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="57a86-125">**속성** 창에서 **DirectQueryMode**속성을 다음 값 중 하나로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-125">In the **Properties** pane, change the property, **DirectQueryMode**, to one of these values:</span></span>  
  
    -   <span data-ttu-id="57a86-126">**DirectQuery 전용**</span><span class="sxs-lookup"><span data-stu-id="57a86-126">**DirectQuery Only**</span></span>  
  
    -   <span data-ttu-id="57a86-127">**InMemory with DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="57a86-127">**InMemory with DirectQuery**</span></span>  
  
    -   <span data-ttu-id="57a86-128">**InMemory를 사용 하는 DirectQuery**</span><span class="sxs-lookup"><span data-stu-id="57a86-128">**DirectQuery with InMemory**</span></span>  
  
 <span data-ttu-id="57a86-129">이러한 속성은 Visual Studio에서 배포 전에 프로젝트에 대해 설정한 속성과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-129">Note that these properties are the same as the properties that you set on the project before deployment in Visual Studio.</span></span> <span data-ttu-id="57a86-130">DirectQuery 사용을 지원하도록 모델을 구성한 경우 언제든지 DirectQuery 모드의 기본 연결 모드를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a86-130">You can change the preferred connection mode for DirectQuery mode at any time, provided that you have configured the model to support DirectQuery usage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57a86-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57a86-131">See Also</span></span>  
 <span data-ttu-id="57a86-132">[DirectQuery 모드 &#40;SSAS 테이블 형식&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="57a86-132">[DirectQuery Mode &#40;SSAS Tabular&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="57a86-133">SSAS 테이블 형식&#41;&#40;DirectQuery 디자인 모드를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="57a86-133">Enable DirectQuery Design Mode &#40;SSAS Tabular&#41;</span></span>](tabular-models/enable-directquery-mode-in-ssdt.md)  
  
  
