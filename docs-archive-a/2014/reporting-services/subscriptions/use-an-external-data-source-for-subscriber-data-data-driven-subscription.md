---
title: 구독자 데이터에 외부 데이터 원본 사용(데이터 기반 구독) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriber data sources [Reporting Services]
- subscriptions [Reporting Services], external data sources
- query-based subscriptions [Reporting Services]
- external data sources [Reporting Services]
- data-driven subscriptions
- data sources [Reporting Services], subscriptions
ms.assetid: 1cade8ec-729c-4df8-a428-e75c9ad86369
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e23da709289ffb6ca345bb6211f40388877a1a87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739082"
---
# <a name="use-an-external-data-source-for-subscriber-data-data-driven-subscription"></a><span data-ttu-id="78c25-102">구독자 데이터에 외부 데이터 원본 사용(데이터 기반 구독)</span><span class="sxs-lookup"><span data-stu-id="78c25-102">Use an External Data Source for Subscriber Data (Data-Driven Subscription)</span></span>
  <span data-ttu-id="78c25-103">데이터 기반 구독에서는 외부 데이터 원본에서 데이터를 검색하는 쿼리 또는 명령에 의해 동적 구독 데이터가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-103">In a data-driven subscription, dynamic subscription data is provided by a query or command that retrieves data from an external data source.</span></span> <span data-ttu-id="78c25-104">데이터 기반 구독 처리 요구 사항을 만족하는 지원되는 모든 데이터 원본에서 구독 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-104">Subscription data can be retrieved from any supported data source that meets the requirements for data-driven subscription processing.</span></span> <span data-ttu-id="78c25-105">쿼리 또는 명령 구문은 보고서 서버와 함께 설치되는 데이터 처리 확장 프로그램에 유효해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-105">The query or command syntax must be valid for a data processing extension installed with your report server.</span></span>  
  
## <a name="data-processing-requirements"></a><span data-ttu-id="78c25-106">데이터 처리 요구 사항</span><span class="sxs-lookup"><span data-stu-id="78c25-106">Data Processing Requirements</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="78c25-107">에서는 데이터 처리 확장 프로그램을 사용하여 구독 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-107">uses data processing extensions to retrieve subscription data.</span></span> <span data-ttu-id="78c25-108">권장되는 데이터 원본 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-108">Recommended data source types include the following:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="78c25-109">관계형 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="78c25-109">relational databases</span></span>  
  
-   <span data-ttu-id="78c25-110">Oracle 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="78c25-110">Oracle databases</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="78c25-111">다차원 및 데이터 마이닝 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="78c25-111">multidimensional and data mining data sources</span></span>  
  
-   <span data-ttu-id="78c25-112">XML 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="78c25-112">XML data sources</span></span>  
  
     <span data-ttu-id="78c25-113">구독자 데이터에 XML 데이터 처리 확장 프로그램을 사용할 때는 구독에서 쿼리 제한 시간 설정을 늘려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-113">When using the XML data processing extension for subscriber data, be sure to increase the query timeout settings in the subscription.</span></span> <span data-ttu-id="78c25-114">XML 데이터 처리 확장 프로그램은 쿼리 제한 시간 값에 초가 아닌 밀리초를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-114">The XML data processing extension uses milliseconds rather than seconds for query timeout values.</span></span> <span data-ttu-id="78c25-115">제한 시간 값을 늘리지 않으면 처리 시간 부족으로 인해 구독이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-115">If you do not increase the timeout value, the subscription might fail due to insufficient processing time.</span></span>  
  
     <span data-ttu-id="78c25-116">구독자 데이터 원본에 대한 연결을 구성할 때 **자격 증명 필요 없음** 옵션을 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="78c25-116">Avoid using the **Credentials are not required** option when configuring the connection to the subscriber data source.</span></span> <span data-ttu-id="78c25-117">XML 데이터 처리 확장 프로그램을 사용하여 런타임에 구독 데이터를 검색하는 경우에는 저장된 자격 증명을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-117">Stored credentials are recommended when using the XML data processing extension to retrieve subscription data at run time.</span></span>  
  
 <span data-ttu-id="78c25-118">지원되는 다른 데이터 원본 유형을 사용할 수 있지만 이 중 일부는 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-118">You might be able to use other supported data source types, but not all of them are guaranteed to work.</span></span> <span data-ttu-id="78c25-119">예를 들어 다음 데이터 원본 유형은 구독자 데이터에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-119">For example, the following data source types cannot be used for subscriber data:</span></span>  
  
-   <span data-ttu-id="78c25-120">SAP Netweaver BI 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="78c25-120">SAP Netweaver BI databases</span></span>  
  
-   <span data-ttu-id="78c25-121">보고서 모델</span><span class="sxs-lookup"><span data-stu-id="78c25-121">report models</span></span>  
  
 <span data-ttu-id="78c25-122">데이터 기반 구독에 사용할 사용자 지정 데이터 처리 확장 프로그램이 있을 경우 해당 프로그램에서는 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> 및 <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> 인터페이스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-122">If you have a custom data processing extension that you want to use in data-driven subscriptions, it must implement the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> and the <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> interfaces.</span></span> <span data-ttu-id="78c25-123">데이터 처리 확장 프로그램에서는 스키마 전용 쿼리 실행을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-123">The data processing extension must support a schema-only query execution.</span></span> <span data-ttu-id="78c25-124">이 쿼리는 사용자가 열을 구독 정의에 있는 배달 옵션 및 보고서 매개 변수에 매핑할 수 있도록 디자인 타임에 열 메타데이터를 검색하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-124">This query is used to retrieve column metadata at design-time so that users can map columns to delivery options and report parameters in the subscription definition.</span></span> <span data-ttu-id="78c25-125">사용자가 구독을 정의할 때는 초기 단계에서 스키마 전용 쿼리가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-125">Schema-only query execution occurs at an early stage when the user is defining the subscription.</span></span>  
  
## <a name="query-requirements"></a><span data-ttu-id="78c25-126">쿼리 요구 사항</span><span class="sxs-lookup"><span data-stu-id="78c25-126">Query Requirements</span></span>  
 <span data-ttu-id="78c25-127">구독 데이터를 검색하는 쿼리를 만들 때 다음 사항을 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="78c25-127">When creating query that retrieves subscription data, keep the following points in mind:</span></span>  
  
-   <span data-ttu-id="78c25-128">구독에 대해 하나의 쿼리만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-128">You can only create one query for the subscription.</span></span>  
  
-   <span data-ttu-id="78c25-129">쿼리에서 배달 옵션 및 보고서 매개 변수 지정에 사용할 값을 모두 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-129">The query must return all of the values that you want to use for delivery options and for specifying report parameters.</span></span>  
  
-   <span data-ttu-id="78c25-130">보고서 서버에서는 결과 집합의 모든 행에 대한 보고서 배달을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-130">The report server will create a report delivery for every row in the result set.</span></span> <span data-ttu-id="78c25-131">결과 집합이 300개의 행으로 구성된 경우에는 보고서 서버에서 300개의 보고서 배달을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-131">If the result set consists of three hundred rows, the report server will attempt to deliver three hundred reports.</span></span>  
  
## <a name="setting-delivery-options-using-variable-data-from-a-subscriber-database"></a><span data-ttu-id="78c25-132">구독자 데이터베이스에서 변수 데이터를 사용하여 배달 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="78c25-132">Setting Delivery Options Using Variable Data from a Subscriber Database</span></span>  
 <span data-ttu-id="78c25-133">구독자 데이터베이스에 있는 데이터를 사용하여 각 받는 사람에 대한 배달 옵션을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-133">You can use data in the subscriber database to customize delivery options for each recipient.</span></span> <span data-ttu-id="78c25-134">사용하는 배달 확장 프로그램 종류에 따라 사용 가능한 옵션이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-134">The kind of delivery extension you are using determines which options are available.</span></span> <span data-ttu-id="78c25-135">보고서 서버 전자 메일 배달 확장 프로그램을 사용하는 경우 쿼리에는 각 구독자에 대한 전자 메일 별칭이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-135">If you are using the report server e-mail delivery extension, the query should contain an e-mail alias for each subscriber.</span></span> <span data-ttu-id="78c25-136">파일 공유 배달을 사용하고 있는 경우 구독자 데이터에는 구독자별 보고서 파일을 만들거나 배달 대상을 제공하는 데 사용할 수 있는 값이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-136">If you are using file share delivery, the subscriber data should include values that can be used to create subscriber-specific report files or to provide a destination for the delivery.</span></span> <span data-ttu-id="78c25-137">자세한 내용은 [Reporting Services의 파일 공유 배달](file-share-delivery-in-reporting-services.md) 및 [Reporting Services에서 전자 메일 배달](e-mail-delivery-in-reporting-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="78c25-137">For more information, see [File Share Delivery in Reporting Services](file-share-delivery-in-reporting-services.md) and [E-Mail Delivery in Reporting Services](e-mail-delivery-in-reporting-services.md).</span></span>  
  
## <a name="passing-parameter-values-from-the-subscriber-database-to-the-report"></a><span data-ttu-id="78c25-138">구독자 데이터베이스에서 보고서로 매개 변수 값 전달</span><span class="sxs-lookup"><span data-stu-id="78c25-138">Passing Parameter Values from the Subscriber Database to the Report</span></span>  
 <span data-ttu-id="78c25-139">매개 변수가 있는 보고서에 대해 데이터 기반 구독을 만드는 경우 변수 매개 변수 값을 사용하여 각 보고서의 출력을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-139">If you are creating a data-driven subscription for a parameterized report, you can use variable parameter values to customize the output of each report.</span></span> <span data-ttu-id="78c25-140">예를 들어 구독자 데이터베이스에는 보고서 데이터를 필터링하는 데 사용할 수 있는 직원 ID 번호, 채용일, 직함, 사무실 위치 정보 등이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-140">For example, the subscriber database might contain employee identification numbers, hire dates, job titles, and office location information that can be used to filter report data.</span></span> <span data-ttu-id="78c25-141">보고서에서 이러한 열 데이터나 기타 사용 가능한 열 데이터를 기반으로 하는 매개 변수를 사용하면 매개 변수를 해당 열로 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-141">If the report accepts parameters that are based on these or other available column data, you can map the parameter to the appropriate column.</span></span>  
  
 <span data-ttu-id="78c25-142">구독자 필드를 보고서 매개 변수에 매핑할 때 데이터 형식과 열 길이는 호환 가능해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-142">When mapping subscriber fields to report parameters, make sure that the data types and column lengths are compatible.</span></span> <span data-ttu-id="78c25-143">데이터 형식이 일치하지 않으면 구독을 처리하는 동안 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-143">If there is a data type mismatch, an error will occur during subscription processing.</span></span> <span data-ttu-id="78c25-144">매개 변수가 있는 보고서에서 구독자 데이터를 사용하는 방법에 대한 자세한 내용은 [데이터 기반 구독 만들기&#40;SSRS 자습서&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="78c25-144">To learn more about using subscriber data in a parameterized report, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md).</span></span>  
  
## <a name="modifying-the-subscriber-data-source"></a><span data-ttu-id="78c25-145">구독자 데이터 원본 수정</span><span class="sxs-lookup"><span data-stu-id="78c25-145">Modifying the Subscriber Data Source</span></span>  
 <span data-ttu-id="78c25-146">구독자 데이터 원본을 다음과 같이 수정하면 구독이 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-146">The following modifications to the subscriber data source can prevent the subscription from running:</span></span>  
  
-   <span data-ttu-id="78c25-147">구독에 참조된 열 제거</span><span class="sxs-lookup"><span data-stu-id="78c25-147">Removing columns that are referenced in the subscription.</span></span>  
  
-   <span data-ttu-id="78c25-148">데이터 원본의 테이블 구조 수정</span><span class="sxs-lookup"><span data-stu-id="78c25-148">Modifying the table structure of the data source.</span></span>  
  
-   <span data-ttu-id="78c25-149">데이터 형식 및 기타 열 속성 변경</span><span class="sxs-lookup"><span data-stu-id="78c25-149">Changing data type and other column properties.</span></span>  
  
 <span data-ttu-id="78c25-150">이렇게 변경하는 경우에는 구독을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78c25-150">If you make any of these changes, you must update the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c25-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="78c25-151">See Also</span></span>  
 <span data-ttu-id="78c25-152">[데이터 기반 구독 만들기, 수정 및 삭제](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="78c25-152">[Create, Modify, and Delete a Data-Driven Subscription](data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="78c25-153">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="78c25-153">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="78c25-154">구독 및 배달&#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="78c25-154">Subscriptions and Delivery &#40;Reporting Services&#41;</span></span>](subscriptions-and-delivery-reporting-services.md)  
  
  
