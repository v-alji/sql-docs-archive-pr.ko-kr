---
title: SSIS를 사용 하 여 Analysis Services 관리 작업 자동화 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Execute DDL Task [Analysis Services]
- Analysis Services Processing task
ms.assetid: e960a9a2-80b4-45da-9369-bc560ecdccac
author: minewiskan
ms.author: owend
ms.openlocfilehash: b35e1f07192b396095daafa9e34d73943cebcad2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729964"
---
# <a name="automate-analysis-services-administrative-tasks-with-ssis"></a><span data-ttu-id="275c3-102">SSIS를 사용하여 Analysis Services 관리 태스크 자동화</span><span class="sxs-lookup"><span data-stu-id="275c3-102">Automate Analysis Services Administrative Tasks with SSIS</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="275c3-103">에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] DDL 스크립트 실행, 큐브 및 마이닝 모델 처리 태스크, 데이터 마이닝 쿼리 태스크를 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enables you to automate execution of DDL scripts, cube and mining model processing tasks, and data mining query tasks.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="275c3-104">는 순차 및 병렬 데이터 처리 작업을 구성하기 위해 연결할 수 있는 제어 흐름 및 유지 관리 태스크의 모음으로 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-104">can be thought of as a collection of control flow and maintenance tasks, which can be linked to form sequential and parallel data processing jobs.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="275c3-105">는 데이터 처리 태스크 중에 데이터 정리 작업을 수행하고 여러 다른 데이터 원본의 데이터를 결합하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-105">is designed to perform data cleaning operations during data processing tasks, and to bring together data from different data sources.</span></span> <span data-ttu-id="275c3-106">큐브 및 마이닝 모델 작업 시에는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에서 숫자가 아닌 데이터를 숫자 데이터로 변환할 수 있으며 데이터 값이 예상 범위 안에 포함되도록 만들어 팩트 테이블 및 차원을 채울 무결한 데이터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-106">When working with cubes and mining models, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] can transform non-numeric data to numeric data, and can ensure that data values fall within expected bounds, thus creating clean data from which to populate fact tables and dimensions.</span></span>  
  
## <a name="integration-services-tasks"></a><span data-ttu-id="275c3-107">Integration Services 태스크</span><span class="sxs-lookup"><span data-stu-id="275c3-107">Integration Services Tasks</span></span>  
 <span data-ttu-id="275c3-108">모든 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 태스크 또는 작업에는 제어 흐름 요소 및 데이터 흐름 요소의 두 가지 주요 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-108">There are two main elements in any [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] task or job: control flow elements and data flow elements.</span></span> <span data-ttu-id="275c3-109">제어 흐름 요소는 선행 제약 조건을 적용하여 작업 처리 과정의 논리적 순서를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-109">The control flow elements define the logical ordering of job progression by applying precedence constraints.</span></span> <span data-ttu-id="275c3-110">데이터 흐름 요소는 구성 요소의 출력과 다음 구성 요소의 입력 간의 연결 및 이 연결 사이의 데이터에서 수행되는 모든 데이터 변환을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-110">The data flow elements concern connectivity between the output of a component to the input of the following component, plus any data transform that might operate on that data in between.</span></span> <span data-ttu-id="275c3-111">데이터 흐름 방향은 출력을 받을 구성 요소를 지정하는 논리가 포함된 선행 제약 조건에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-111">As for the decision about where the data goes, precedence constraints contain logic to specify which component receives the output.</span></span> <span data-ttu-id="275c3-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 가장 적합 한 태스크에는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 실행 태스크, Analysis Services 처리 태스크 및 데이터 마이닝 쿼리 태스크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-112">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tasks that are most relevant to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] include the Execute DDL Task, the Analysis Services Processing Task, and the Data Mining Query Task.</span></span> <span data-ttu-id="275c3-113">이러한 각 태스크에 대해 메일 보내기 작업을 사용하여 관리자에게 작업 결과가 포함된 전자 메일 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-113">For each of these tasks, the Send Mail Task can be used to send the administrator an e-mail message containing the task results.</span></span>  
  
## <a name="the-execute-ddl-task"></a><span data-ttu-id="275c3-114">DDL 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="275c3-114">The Execute DDL Task</span></span>  
 <span data-ttu-id="275c3-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 의 DDL 실행 태스크를 사용하여 DDL 스크립트를 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버로 직접 보내고 자동으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-115">The Execute DDL Task in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enables you to send DDL scripts directly to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server and to run them automatically.</span></span> <span data-ttu-id="275c3-116">이렇게 하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 관리자가 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 내에서 백업, 복원 또는 동기화 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-116">This allows the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator to perform backup, restore, or sync operations from within an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="275c3-117">패키지는 앞에서 설명한 제어 흐름 요소와 데이터 흐름 요소로 구성되어 있으며 이러한 모든 요소는 태스크에 추가할 수 있는 다른 DDL 문과 같이 **run regularly**여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-117">A package is made up of the control and data flow elements described earlier, which all must be **run regularly**, as do other DDL statements that can be added to tasks.</span></span> <span data-ttu-id="275c3-118">여기서 설명하는 태스크는 종종 야간에 실행되기 때문에 예약 애플리케이션에서 쉽게 실행할 수 있는 패키지가 있으면 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-118">Because the tasks discussed here are frequently run at night, it is particularly useful to have packages that can easily be run from any scheduling application.</span></span> <span data-ttu-id="275c3-119">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 에이전트를 사용하여 언제든지 패키지가 실행되도록 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-119">You can schedule a package to be run at any time using [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Agent.</span></span> <span data-ttu-id="275c3-120">이 태스크의 구현 방법은 [Analysis Services DDL 실행 태스크](../../integration-services/control-flow/analysis-services-execute-ddl-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="275c3-120">For more information about how to implement this task, see [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md).</span></span>  
  
## <a name="analysis-services-processing-task"></a><span data-ttu-id="275c3-121">Analysis Services 처리 태스크</span><span class="sxs-lookup"><span data-stu-id="275c3-121">Analysis Services Processing Task</span></span>  
 <span data-ttu-id="275c3-122">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 의 Analysis Services 처리 태스크를 사용하여 원본 관계형 데이터베이스를 정기적으로 업데이트할 때 자동으로 큐브를 새 정보로 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-122">The Analysis Services Processing Task in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enables you to automatically populate cubes with new information when you make regular updates to your source relational database.</span></span> <span data-ttu-id="275c3-123">Analysis Services 처리 태스크를 사용하여 차원, 큐브 또는 파티션 수준에서 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-123">You can process at the dimension, cube, or partition level using the Analysis Services Processing Task.</span></span> <span data-ttu-id="275c3-124">작업 요구 사항에 따라 처리 자체의 유형을 `incremental` 또는 `full`로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-124">The processing itself can be of type `incremental` or `full`, which you select based on your job requirements.</span></span> <span data-ttu-id="275c3-125">증분 처리는 새 데이터를 추가하고 충분히 다시 계산하여 대상을 최신 상태로 유지하는 반면 전체 처리는 기존 데이터를 삭제하여 대상을 완전히 다시 로드 및 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-125">Incremental processing adds new data and performs enough recalculation to keep the target up-to-date, whereas full processing drops existing data for a complete reload and recalculation.</span></span> <span data-ttu-id="275c3-126">전체 처리는 많은 시간이 소요되지만 보다 완전합니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-126">Full processing takes more time, but is more complete.</span></span> <span data-ttu-id="275c3-127">이 태스크의 구현 방법은 [Analysis Services Processing Task](../../integration-services/control-flow/analysis-services-processing-task.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="275c3-127">For more information about how to implement this task, see [Analysis Services Processing Task](../../integration-services/control-flow/analysis-services-processing-task.md).</span></span>  
  
## <a name="data-mining-query-task"></a><span data-ttu-id="275c3-128">Data Mining Query Task</span><span class="sxs-lookup"><span data-stu-id="275c3-128">Data Mining Query Task</span></span>  
 <span data-ttu-id="275c3-129">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 의 데이터 마이닝 쿼리 태스크를 사용하여 마이닝 모델에서 정보를 추출 및 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-129">The Data Mining Query Task in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enables you to extract and store information from mining models.</span></span> <span data-ttu-id="275c3-130">이러한 정보는 종종 관계형 데이터베이스에 저장되며 대상 마케팅 캠페인을 위해 잠재적인 고객 목록을 구분하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-130">The information is often stored in a relational database and, for example, can be used to isolate a list of potential customers for a targeted marking campaign.</span></span> <span data-ttu-id="275c3-131">데이터 마이닝을 통해 고객의 가치 및 고객이 특정 마케팅 전략에 응답할 확률을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-131">Data mining can identify the value of a customer and the probability that the customer will respond to a particular marketing pitch.</span></span> <span data-ttu-id="275c3-132">또한 데이터 마이닝 쿼리 태스크를 사용하여 데이터를 원하는 형식으로 추출 및 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="275c3-132">You can use the Data Mining Query Task to extract and modify data to a preferred format.</span></span> <span data-ttu-id="275c3-133">이 태스크의 구현 방법은 [Data Mining Query Task](../../integration-services/control-flow/data-mining-query-task.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="275c3-133">For more information about how to implement this task, see [Data Mining Query Task](../../integration-services/control-flow/data-mining-query-task.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="275c3-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="275c3-134">See Also</span></span>  
 <span data-ttu-id="275c3-135">[파티션 처리 대상](../../integration-services/data-flow/partition-processing-destination.md) </span><span class="sxs-lookup"><span data-stu-id="275c3-135">[Partition Processing Destination](../../integration-services/data-flow/partition-processing-destination.md) </span></span>  
 <span data-ttu-id="275c3-136">[차원 처리 대상](../../integration-services/data-flow/dimension-processing-destination.md) </span><span class="sxs-lookup"><span data-stu-id="275c3-136">[Dimension Processing Destination](../../integration-services/data-flow/dimension-processing-destination.md) </span></span>  
 <span data-ttu-id="275c3-137">[데이터 마이닝 쿼리 변환](../../integration-services/data-flow/transformations/data-mining-query-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="275c3-137">[Data Mining Query Transformation](../../integration-services/data-flow/transformations/data-mining-query-transformation.md) </span></span>  
 <span data-ttu-id="275c3-138">[다차원 모델 개체 처리](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="275c3-138">[Multidimensional Model Object Processing](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md) </span></span>  
 [<span data-ttu-id="275c3-139">Analysis Services의 스크립트 관리 태스크</span><span class="sxs-lookup"><span data-stu-id="275c3-139">Script Administrative Tasks in Analysis Services</span></span>](../script-administrative-tasks-in-analysis-services.md)  
  
  