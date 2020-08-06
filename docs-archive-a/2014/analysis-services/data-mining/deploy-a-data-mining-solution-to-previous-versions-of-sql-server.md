---
title: 이전 버전의 SQL Server에 데이터 마이닝 솔루션 배포 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [Analysis Services]
- holdout [data mining]
- deploy [Analysis Services]
- time series [Analysis Services]
- deploying [Analysis Services - data mining]
- synchronization [Analysis Services]
- deployment [Analysis Services]
ms.assetid: 2715c245-f206-43af-8bf5-e6bd2585477a
author: minewiskan
ms.author: owend
ms.openlocfilehash: f09a37c078cf58f24db9a08e3ddcb68cb2638717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659733"
---
# <a name="deploy-a-data-mining-solution-to-previous-versions-of-sql-server"></a><span data-ttu-id="979ce-102">데이터 마이닝 솔루션을 이전 버전의 SQL Server에 배포</span><span class="sxs-lookup"><span data-stu-id="979ce-102">Deploy a Data Mining Solution to Previous Versions of SQL Server</span></span>
  <span data-ttu-id="979ce-103">이 섹션에서는 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 인스턴스에서 만든 데이터 마이닝 모델이나 데이터 마이닝 구조를 SQL Server 2005 Analysis Services를 사용하는 데이터베이스에 배포하려고 하거나 SQL Server 2005에서 만든 모델을 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]인스턴스에 배포할 때 발생할 수 있는 알려진 호환성 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-103">This section describes known compatibility issues that may arise when you attempt to deploy a data mining model or data mining structure that was created in an instance of [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] to a database that uses SQL Server 2005 Analysis Services, or when you deploy models created in SQL Server 2005 to an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="979ce-104">SQL Server 2000 Analysis Services 인스턴스로의 배포는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-104">Deployment to an instance of SQL Server 2000 Analysis Services is not supported.</span></span>  
  
 [<span data-ttu-id="979ce-105">시계열 모델 배포</span><span class="sxs-lookup"><span data-stu-id="979ce-105">Deploying Time Series Models</span></span>](#bkmk_TimeSeries)  
  
 [<span data-ttu-id="979ce-106">홀드 아웃이 있는 모델 배포</span><span class="sxs-lookup"><span data-stu-id="979ce-106">Deploying Models with Holdout</span></span>](#bkmk_Holdout)  
  
 [<span data-ttu-id="979ce-107">필터를 사용 하 여 모델 배포</span><span class="sxs-lookup"><span data-stu-id="979ce-107">Deploying Models with Filters</span></span>](#bkmk_Filter)  
  
 [<span data-ttu-id="979ce-108">데이터베이스 백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="979ce-108">Restoring from Database Backups</span></span>](#bkmk_Backup)  
  
 [<span data-ttu-id="979ce-109">데이터베이스 동기화 사용</span><span class="sxs-lookup"><span data-stu-id="979ce-109">Using Database Synchronization</span></span>](#bkmk_Synch)  
  
##  <a name="deploying-times-series-models"></a><a name="bkmk_TimeSeries"></a><span data-ttu-id="979ce-110">시계열 모델 배포</span><span class="sxs-lookup"><span data-stu-id="979ce-110">Deploying Times Series Models</span></span>  
 <span data-ttu-id="979ce-111">SQL Server 2008에서는 보조 알고리즘인 ARIMA가 추가되어 Microsoft Time Series 알고리즘이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-111">The Microsoft Time Series algorithm was enhanced in SQL Server 2008 by the addition of a second, complementary algorithm, ARIMA.</span></span> <span data-ttu-id="979ce-112">Time Series 알고리즘의 변경 사항에 대한 자세한 내용은 [Microsoft Time Series 알고리즘](microsoft-time-series-algorithm.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="979ce-112">For more information about the changes in the time series algorithm, see [Microsoft Time Series Algorithm](microsoft-time-series-algorithm.md).</span></span>  
  
 <span data-ttu-id="979ce-113">따라서 새 ARIMA 알고리즘을 사용하는 시계열 마이닝 모델이 SQL Server 2005 Analysis Services 인스턴스에 배포될 경우 다르게 동작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-113">Therefore, time series mining models that use the new ARIMA algorithm may behave differently when deployed to an instance of SQL Server 2005 Analysis Services.</span></span>  
  
 <span data-ttu-id="979ce-114">예측에서 ARTXP 및 ARIMA 모델의 혼합 사용을 제어하기 위해 PREDICTION_SMOOTHING 매개 변수를 명시적으로 설정한 경우 이 모델을 SQL Server 2005 인스턴스에 배포하면 Analysis Services에서 매개 변수가 유효하지 않다는 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-114">If you have explicitly set the parameter PREDICTION_SMOOTHING to control the mixture of ARTXP and ARIMA models in prediction, when you deploy this model to an instance of SQL Server 2005, Analysis Services will raise an error stating that the parameter is not valid.</span></span> <span data-ttu-id="979ce-115">이 오류를 방지하려면 PREDICTION_SMOOTHING 매개 변수를 삭제하고 모델을 순수한 ARTXP 모델로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-115">To prevent this error, you must delete the PREDICTION_SMOOTHING parameter and convert the models to a pure ARTXP model.</span></span>  
  
 <span data-ttu-id="979ce-116">반대로 SQL Server 2005 Analysis Services를 사용하여 만든 시계열 모델을 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]인스턴스에 배포한 경우 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 마이닝 모델을 열면 먼저 정의 파일이 새 형식으로 변환되고 두 개의 새 매개 변수가 기본적으로 모든 시계열 모델에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-116">Conversely, if you deploy a time series model that was created using SQL Server 2005 Analysis Services to an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], when you open the mining model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the definition files are first converted to the new format, and two new parameters are added by default to all time series models.</span></span> <span data-ttu-id="979ce-117">FORECAST_METHOD 매개 변수와 PREDICTION_SMOOTHING 매개 변수는 각각 기본값인 MIXED와 0.5를 사용하여 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-117">The parameter FORECAST_METHOD is added with the default value of MIXED, and the parameter PREDICTION_SMOOTHING is added with the default value of 0.5.</span></span> <span data-ttu-id="979ce-118">그러나 모델을 다시 처리할 때까지 모델에서는 계속 ARTXP만 예측에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-118">However, the model will continue to use only ARTXP for forecasting until you reprocess the model.</span></span> <span data-ttu-id="979ce-119">모델을 다시 처리하면 ARIMA와 ARTXP를 둘 다 사용하도록 모델이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-119">As soon as you reprocess the model, prediction changes to use both ARIMA and ARTXP.</span></span>  
  
 <span data-ttu-id="979ce-120">따라서 모델을 변경하지 않으려면 모델을 탐색만 해야 하고 처리하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-120">Therefore, if you wish to avoid changing the model, you should only browse the model and never process it.</span></span> <span data-ttu-id="979ce-121">또는 FORECAST_METHOD 또는 PREDICTION_SMOOTHING 매개 변수를 명시적으로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-121">Alternatively, you could explicitly set the FORECAST_METHOD or PREDICTION_SMOOTHING parameters.</span></span>  
  
 <span data-ttu-id="979ce-122">혼합 모델을 구성하는 방법에 대한 자세한 내용은 [Microsoft Time Series 알고리즘 기술 참조](microsoft-time-series-algorithm-technical-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="979ce-122">For detailed information about configuring mixed models, see [Microsoft Time Series Algorithm Technical Reference](microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="979ce-123">모델의 데이터 원본에 사용되는 공급자가 SQL Client Data Provider 10이면 데이터 원본 정의도 수정하여 이전 버전의 SQL Server Native Client를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-123">If the provider that is used for the model's data source is SQL Client Data Provider 10, you must also modify the data source definition to specify the previous version of the SQL Server Native Client.</span></span> <span data-ttu-id="979ce-124">그렇지 않으면 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 에서 공급자가 등록되지 않았다는 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-124">Otherwise, [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] generates an error stating that the provider is not registered.</span></span>  
  
##  <a name="deploying-models-with-holdout"></a><a name="bkmk_Holdout"></a> <span data-ttu-id="979ce-125">홀드아웃이 있는 모델 배포</span><span class="sxs-lookup"><span data-stu-id="979ce-125">Deploying Models with Holdout</span></span>  
 <span data-ttu-id="979ce-126">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 를 사용하여 데이터 마이닝 모델의 테스트에 사용되는 홀드아웃 파티션이 포함된 마이닝 구조를 만들면 이 마이닝 구조를 SQL Server 2005 인스턴스에 배포할 수 있지만 파티션 정보는 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-126">If you use [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] to create a mining structure that contains a holdout partition used for testing data mining models, the mining structure can be deployed to an instance of SQL Server 2005, but the partition information will be lost.</span></span>  
  
 <span data-ttu-id="979ce-127">SQL Server 2005 Analysis Services에서 마이닝 구조를 열면 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 에서 오류가 발생하고 홀드아웃 파티션이 제거된 구조가 다시 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-127">When you open the mining structure in SQL Server 2005 Analysis Services, [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] raises an error, and then regenerates the structure to remove the holdout partition.</span></span>  
  
 <span data-ttu-id="979ce-128">구조를 다시 작성 한 후에는 홀드 아웃 파티션의 크기를 더 이상 속성 창에서 사용할 수 없습니다. 그러나 값 \<ddl100_100:HoldoutMaxPercent> 30)은 \</ddl100_100:HoldoutMaxPercent> 계속 해 서이 파일에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-128">After the structure has been rebuilt, the size of the holdout partition is no longer available in the Properties window; however, the value \<ddl100_100:HoldoutMaxPercent>30\</ddl100_100:HoldoutMaxPercent>) may still be present in the ASSL script file.</span></span>  
  
##  <a name="deploying-models-with-filters"></a><a name="bkmk_Filter"></a> <span data-ttu-id="979ce-129">필터가 있는 모델 배포</span><span class="sxs-lookup"><span data-stu-id="979ce-129">Deploying Models with Filters</span></span>  
 <span data-ttu-id="979ce-130">[!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] 를 사용하여 마이닝 모델에 필터를 적용하는 경우 SQL Server 2005 인스턴스에 모델을 배포할 수 있지만 필터는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-130">If you use [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] to apply a filter to a mining model, the model can be deployed to an instance of SQL Server 2005, but the filter will not be applied.</span></span>  
  
 <span data-ttu-id="979ce-131">마이닝 모델을 열면 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서 오류가 발생하고 필터가 제거된 모델이 다시 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-131">When you open the mining model, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] raises an error, and then regenerates the model to remove the filter.</span></span>  
  
##  <a name="restoring-from-database-backups"></a><a name="bkmk_Backup"></a><span data-ttu-id="979ce-132">데이터베이스 백업에서 복원</span><span class="sxs-lookup"><span data-stu-id="979ce-132">Restoring from Database Backups</span></span>  
 <span data-ttu-id="979ce-133">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 만든 데이터베이스 백업은 SQL Server 2005 인스턴스로 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-133">You cannot restore a database backup that was created in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to an instance of SQL Server 2005.</span></span> <span data-ttu-id="979ce-134">그럴 경우 SQL Server Management Studio에서 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-134">If you do so, SQL Server Management Studio generates an error.</span></span>  
  
 <span data-ttu-id="979ce-135">SQL Server 2005 Analysis Services 데이터베이스의 백업을 만들고 이 백업을 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]인스턴스로 복원하면 모든 시계열 모델이 이전 섹션에서 설명한 대로 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-135">If you create a backup of a SQL Server 2005 Analysis Services database and restore this backup on an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], all time series models are modified as described in the previous section.</span></span>  
  
##  <a name="using-database-synchronization"></a><a name="bkmk_Synch"></a><span data-ttu-id="979ce-136">데이터베이스 동기화 사용</span><span class="sxs-lookup"><span data-stu-id="979ce-136">Using Database Synchronization</span></span>  
 <span data-ttu-id="979ce-137">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 SQL Server 2005로의 데이터베이스 동기화는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-137">Database synchronization is not supported from [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to SQL Server 2005.</span></span>  
  
 <span data-ttu-id="979ce-138">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 데이터베이스를 동기화하려고 하면 서버에서 오류를 반환하고 데이터베이스 동기화가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="979ce-138">If you attempt to synchronize a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] database, the server returns an error and database synchronization fails.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="979ce-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="979ce-139">See Also</span></span>  
 [<span data-ttu-id="979ce-140">Analysis Services 이전 버전과의 호환성</span><span class="sxs-lookup"><span data-stu-id="979ce-140">Analysis Services Backward Compatibility</span></span>](../analysis-services-backward-compatibility.md)  
  
  
