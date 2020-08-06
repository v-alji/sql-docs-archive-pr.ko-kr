---
title: 패키지 실행 및 기타 작업 모니터링 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 628b62d9c8e01d0dc0bf641551de67c3838a4504
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661242"
---
# <a name="monitoring-for-package-executions-and-other-operations"></a><span data-ttu-id="7c214-102">패키지 실행 및 기타 작업 모니터링</span><span class="sxs-lookup"><span data-stu-id="7c214-102">Monitoring for Package Executions and Other Operations</span></span>
  <span data-ttu-id="7c214-103">다음 도구 중 하나 이상을 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 실행, 프로젝트 유효성 검사 및 기타 작업을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c214-103">You can monitor [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package executions, project validations, and other operations by using one of more of the following tools.</span></span> <span data-ttu-id="7c214-104">데이터 탭과 같은 일부 도구는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 배포된 프로젝트에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c214-104">Certain tools such as data taps are available only for projects that are deployed to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
-   <span data-ttu-id="7c214-105">로그</span><span class="sxs-lookup"><span data-stu-id="7c214-105">Logs</span></span>  
  
     <span data-ttu-id="7c214-106">자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](integration-services-ssis-logging.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c214-106">For more information, see [Integration Services &#40;SSIS&#41; Logging](integration-services-ssis-logging.md).</span></span>  
  
-   <span data-ttu-id="7c214-107">보고서</span><span class="sxs-lookup"><span data-stu-id="7c214-107">Reports</span></span>  
  
     <span data-ttu-id="7c214-108">자세한 내용은 [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c214-108">For more information, see [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).</span></span>  
  
-   <span data-ttu-id="7c214-109">뷰</span><span class="sxs-lookup"><span data-stu-id="7c214-109">Views</span></span>  
  
     <span data-ttu-id="7c214-110">자세한 내용은 [뷰&#40;Integration Services 카탈로그&#41;](/sql/integration-services/system-views/views-integration-services-catalog)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c214-110">For more information, see [Views &#40;Integration Services Catalog&#41;](/sql/integration-services/system-views/views-integration-services-catalog).</span></span>  
  
-   <span data-ttu-id="7c214-111">성능 카운터</span><span class="sxs-lookup"><span data-stu-id="7c214-111">Performance counters</span></span>  
  
     <span data-ttu-id="7c214-112">자세한 내용은 [성능 카운터](performance-counters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c214-112">For more information, see [Performance Counters](performance-counters.md).</span></span>  
  
-   <span data-ttu-id="7c214-113">데이터 탭</span><span class="sxs-lookup"><span data-stu-id="7c214-113">Data taps</span></span>  
  
## <a name="operation-types"></a><span data-ttu-id="7c214-114">작업 유형</span><span class="sxs-lookup"><span data-stu-id="7c214-114">Operation Types</span></span>  
 <span data-ttu-id="7c214-115">여러 유형의 작업이 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버의 `SSISDB` 카탈로그에서 모니터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c214-115">Several different types of operations are monitored in the `SSISDB` catalog, on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="7c214-116">각 작업과 연관된 메시지가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c214-116">Each operation can have multiple messages associated with it.</span></span> <span data-ttu-id="7c214-117">각 메시지는 여러 가지 유형 중 하나로 분류될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c214-117">Each message can be classified into one of several different types.</span></span> <span data-ttu-id="7c214-118">예를 들어 정보, 경고 또는 오류 메시지일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c214-118">For example, a message can be of type Information, Warning, or Error.</span></span> <span data-ttu-id="7c214-119">메시지 유형에 대한 전체 목록은 Transact-SQL [catalog.operation_messages&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database) 뷰를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c214-119">For the full list of message types, see the documentation for the Transact-SQL [catalog.operation_messages &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database) view.</span></span> <span data-ttu-id="7c214-120">작업 유형에 대한 전체 목록은 [catalog.operations&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c214-120">For a full list of the operations types, see [catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database).</span></span>  
  
 <span data-ttu-id="7c214-121">한 작업의 상태를 나타내기 위해 9가지 상태 유형이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c214-121">Nine different status types are used to indicate the status of an operation.</span></span> <span data-ttu-id="7c214-122">상태 유형에 대한 전체 목록은 [catalog.operations&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database) 뷰를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7c214-122">For a full list of the status types, see the [catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database) view.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="7c214-123">관련 내용</span><span class="sxs-lookup"><span data-stu-id="7c214-123">Related Content</span></span>  
 <span data-ttu-id="7c214-124">blogs.msdn.com의 블로그 항목, [SSIS T-SQL API 개요](https://go.microsoft.com/fwlink/?LinkId=249051)</span><span class="sxs-lookup"><span data-stu-id="7c214-124">Blog entry, [SSIS T-SQL API Overview](https://go.microsoft.com/fwlink/?LinkId=249051), on blogs.msdn.com.</span></span>  
  
  
