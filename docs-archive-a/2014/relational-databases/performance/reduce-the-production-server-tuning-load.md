---
title: 프로덕션 서버 튜닝 로드 줄이기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- overhead [Database Engine Tuning Advisor]
- tuning overhead [SQL Server]
- reducing production server tuning load
- Database Engine Tuning Advisor [SQL Server], test servers
- test servers [Database Engine Tuning Advisor]
- production servers [SQL Server]
- offload tuning overhead [SQL Server]
ms.assetid: bb95ecaf-444a-4771-a625-e0a91c8f0709
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 53a61b17793a50d6b819f7c1684afdc4de4377f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652778"
---
# <a name="reduce-the-production-server-tuning-load"></a><span data-ttu-id="305b5-102">프로덕션 서버 튜닝 로드 줄이기</span><span class="sxs-lookup"><span data-stu-id="305b5-102">Reduce the Production Server Tuning Load</span></span>
  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="305b5-103">튜닝 관리자는 쿼리 최적화 프로그램을 사용하여 작업을 분석하고 튜닝 권장 사항을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-103">Tuning Advisor relies on the query optimizer to analyze a workload and to make tuning recommendations.</span></span> <span data-ttu-id="305b5-104">프로덕션 서버에서 이러한 분석을 수행하면 서버 부하가 가중되어 튜닝 세션 중에 서버 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-104">Performing this analysis on the production server adds to the server load and can hurt server performance during the tuning session.</span></span> <span data-ttu-id="305b5-105">프로덕션 서버 외에 추가로 테스트 서버를 사용하면 튜닝 세션 중에 서버 부하에 미치는 영향을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-105">You can reduce the impact to the server load during a tuning session by using a test server in addition to the production server.</span></span>

## <a name="how-database-engine-tuning-advisor-uses-a-test-server"></a><span data-ttu-id="305b5-106">데이터베이스 엔진 튜닝 관리자가 테스트 서버를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="305b5-106">How Database Engine Tuning Advisor Uses a Test Server</span></span>
 <span data-ttu-id="305b5-107">테스트 서버를 사용하는 일반적인 방법은 프로덕션 서버에서 테스트 서버로 데이터를 모두 복사하고 테스트 서버를 튜닝한 다음 프로덕션 서버에 권장 사항을 구현하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-107">The traditional way to use a test server is to copy all of the data from your production server to your test server, tune the test server, and then implement the recommendation on your production server.</span></span> <span data-ttu-id="305b5-108">이 작업으로 프로덕션 서버의 성능에 미치는 영향을 없앨 수는 있지만 최적의 방법은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-108">This process eliminates the performance impact on your production server, but nevertheless is not the optimal solution.</span></span> <span data-ttu-id="305b5-109">예를 들어 프로덕션 서버에서 테스트 서버로 많은 양의 데이터를 복사하는 데 상당한 시간과 리소스가 소비될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-109">For example, copying large amounts of data from the production to the test server can consume substantial amounts of time and resources.</span></span> <span data-ttu-id="305b5-110">또한 테스트 서버 하드웨어의 성능은 프로덕션 서버 하드웨어 보다 뒤쳐지는 것이 보통입니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-110">In addition, test server hardware is seldom as powerful as the hardware that is deployed for production servers.</span></span> <span data-ttu-id="305b5-111">튜닝 프로세스는 쿼리 최적화 프로그램에 의존하며 이 프로세스에서 생성하는 권장 사항의 일부는 기반 하드웨어를 바탕으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-111">The tuning process relies on the query optimizer, and the recommendations it generates are based in part on the underlying hardware.</span></span> <span data-ttu-id="305b5-112">테스트 서버와 프로덕션 서버 하드웨어가 동일하지 않은 경우 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 튜닝 관리자의 권장 사항은 정확성이 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-112">If the test and production server hardware are not identical, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor recommendation quality is diminished.</span></span>

 <span data-ttu-id="305b5-113">이러한 문제를 피하기 위해 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 튜닝 관리자는 대부분의 튜닝 부하를 테스트 서버로 오프로드하여 프로덕션 서버의 데이터베이스를 튜닝합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-113">To avoid these problems, [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor tunes a database on a production server by offloading most of the tuning load onto a test server.</span></span> <span data-ttu-id="305b5-114">이 작업은 실제로 프로덕션 서버에서 테스트 서버로 데이터를 복사하지 않고 프로덕션 서버의 하드웨어 구성 정보를 이용해 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-114">It does this by using the production server hardware configuration information and without actually copying the data from the production server to the test server.</span></span> [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="305b5-115">튜닝 관리자는 실제로 데이터를 프로덕션 서버에서 테스트 서버로 복사하지 않고</span><span class="sxs-lookup"><span data-stu-id="305b5-115">Tuning Advisor does not copy actual data from the production server to the test server.</span></span> <span data-ttu-id="305b5-116">메타데이터와 필요한 통계만 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-116">It only copies the metadata and necessary statistics.</span></span>

 <span data-ttu-id="305b5-117">다음 절차는 테스트 서버에서 프로덕션 서버를 튜닝하는 프로세스를 개략적으로 설명한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-117">The following steps outline the process for tuning a production database on a test server:</span></span>

1.  <span data-ttu-id="305b5-118">테스트 서버를 사용하려는 사용자가 양쪽 서버에 존재하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-118">Make sure that the user who wants to use the test server exists on both servers.</span></span>

     <span data-ttu-id="305b5-119">시작하기 전에 프로덕션 서버의 데이터베이스를 테스트 서버에서 튜닝하려는 사용자가 양쪽 서버에 존재하는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="305b5-119">Before you start, make sure that the user who wants to use the test server to tune a database on the production server exists on both servers.</span></span> <span data-ttu-id="305b5-120">이를 위해서는 테스트 서버에 사용자와 사용자 로그인을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-120">This requires that you create the user and his or her login on the test server.</span></span> <span data-ttu-id="305b5-121">사용자가 양쪽 컴퓨터에서 **sysadmin** 고정 서버 역할의 멤버인 경우 이 단계는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-121">If you are a member of the **sysadmin** fixed server role on both computers, this step is not necessary.</span></span>

2.  <span data-ttu-id="305b5-122">테스트 서버에서 작업을 튜닝합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-122">Tune the workload on the test server.</span></span>

     <span data-ttu-id="305b5-123">테스트 서버에서 작업을 튜닝하려면 **dta** 명령줄 유틸리티가 있는 XML 입력 파일을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-123">To tune a workload on a test server, you must use an XML input file with the **dta** command-line utility.</span></span> <span data-ttu-id="305b5-124">XML 입력 파일에서 **TuningOptions** 부모 요소의 **TestServer** 하위 요소에 테스트 서버의 이름을 지정하고 기타 다른 하위 요소에 대해서도 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-124">In the XML input file, specify the name of your test server with the **TestServer** subelement in addition to specifying the values for the other subelements under the **TuningOptions** parent element.</span></span>

     <span data-ttu-id="305b5-125">튜닝 프로세스 중에 데이터베이스 엔진 튜닝 관리자가 테스트 서버에 셸 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-125">During the tuning process, Database Engine Tuning Advisor creates a shell database on the test server.</span></span> <span data-ttu-id="305b5-126">셸 데이터베이스를 만들고 튜닝하기 위해 데이터베이스 엔진 튜닝 관리자는 프로덕션 서버를 호출하여 다음과 같은 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-126">To create this shell database and tune it, Database Engine Tuning Advisor makes calls to the production server for the following:</span></span>

    1.  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="305b5-127">튜닝 관리자가 프로덕션 데이터베이스에서 테스트 서버 셸 데이터베이스로 메타데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-127">Tuning Advisor imports metadata from the production database to the test server shell database.</span></span> <span data-ttu-id="305b5-128">이 메타데이터에는 빈 테이블, 인덱스, 뷰, 저장 프로시저, 트리거 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-128">This metadata includes empty tables, indexes, views, stored procedures, triggers, and so on.</span></span> <span data-ttu-id="305b5-129">이 메타데이터를 이용하면 작업 쿼리를 프로덕션 데이터베이스가 아닌 테스트 서버 셸 데이터베이스에 대해 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-129">This makes it possible for the workload queries to execute against the test server shell database.</span></span>

    2.  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="305b5-130">튜닝 관리자가 프로덕션 서버에서 통계를 가져와 쿼리 최적화 프로그램이 테스트 서버에서 쿼리를 정확하게 최적화할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-130">Tuning Advisor imports statistics from the production server so the query optimizer can accurately optimize queries on the test server.</span></span>

    3.  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] <span data-ttu-id="305b5-131">튜닝 관리자가 프로덕션 서버의 프로세서 수와 사용 가능한 메모리를 지정하는 하드웨어 매개 변수를 가져와 쿼리 최적화 프로그램에 쿼리 계획을 생성하는 데 필요한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-131">Tuning Advisor imports hardware parameters specifying the number of processors and available memory from the production server to provide the query optimizer with the information it needs to generate a query plan.</span></span>

3.  <span data-ttu-id="305b5-132">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 튜닝 관리자가 테스트 서버 셸 데이터베이스 튜닝을 완료한 후 튜닝 권장 사항을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-132">After [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor finishes tuning the test server shell database, it generates a tuning recommendation.</span></span>

4.  <span data-ttu-id="305b5-133">테스트 서버를 튜닝하여 얻은 권장 사항을 프로덕션 서버에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-133">Apply the recommendation received from tuning the test server to the production server.</span></span>

 <span data-ttu-id="305b5-134">다음 그림은 테스트 서버 및 프로덕션 서버 시나리오를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-134">The following illustration shows the test server and production server scenario:</span></span>

 <span data-ttu-id="305b5-135">![데이터베이스 엔진 튜닝 관리자의 테스트 서버 사용](../../database-engine/media/testsvr.gif "데이터베이스 엔진 튜닝 관리자의 테스트 서버 사용")</span><span class="sxs-lookup"><span data-stu-id="305b5-135">![Database Engine Tuning Advisor test server usage](../../database-engine/media/testsvr.gif "Database Engine Tuning Advisor test server usage")</span></span>

> [!NOTE]
>  <span data-ttu-id="305b5-136">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 튜닝 관리자 GUI(그래픽 사용자 인터페이스)에서는 테스트 서버 튜닝 기능이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-136">The test server tuning feature is not supported in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor graphical user interface (GUI).</span></span>

## <a name="example"></a><span data-ttu-id="305b5-137">예제</span><span class="sxs-lookup"><span data-stu-id="305b5-137">Example</span></span>
 <span data-ttu-id="305b5-138">우선 튜닝 작업을 수행하려는 사용자가 테스트 서버와 프로덕션 서버에 모두 존재하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-138">First, make sure that the user who wants to perform the tuning exists on both the test and production servers.</span></span>

 <span data-ttu-id="305b5-139">사용자 정보를 테스트 서버로 복사한 후 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 튜닝 관리자 XML 입력 파일에 테스트 서버 튜닝 세션을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-139">After the user information is copied over to your test server, you can define your test server tuning session in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor XML input file.</span></span> <span data-ttu-id="305b5-140">다음 XML 입력 파일 예에서는 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 튜닝 관리자로 데이터베이스를 튜닝하도록 테스트 서버를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-140">The following example XML input file illustrates how to specify a test server to tune a database with [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor.</span></span>

 <span data-ttu-id="305b5-141">이 예에서는 `MyDatabaseName` 에서 `MyServerName`데이터베이스가 튜닝되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-141">In this example, the `MyDatabaseName` database is being tuned on `MyServerName`.</span></span> <span data-ttu-id="305b5-142">[!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트인 `MyWorkloadScript.sql`이 작업으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-142">The [!INCLUDE[tsql](../../includes/tsql-md.md)] script, `MyWorkloadScript.sql`, is used as the workload.</span></span> <span data-ttu-id="305b5-143">이 작업에는 `MyDatabaseName`에 대해 실행되는 이벤트가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-143">This workload contains events that execute against `MyDatabaseName`.</span></span> <span data-ttu-id="305b5-144">튜닝 프로세스의 일부로 발생하는 이 데이터베이스에 대한 쿼리 최적화 프로그램 호출 중 대부분은 `MyTestServerName`에 있는 셸 데이터베이스에 의해 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-144">Most of the query optimizer calls to this database, which occur as part of the tuning process, are handled by the shell database that resides on `MyTestServerName`.</span></span> <span data-ttu-id="305b5-145">셸 데이터베이스는 메타데이터와 통계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-145">The shell database is composed of metadata and statistics.</span></span> <span data-ttu-id="305b5-146">이 작업 결과로 튜닝 오버헤드가 테스트 서버로 오프로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-146">This process results in the tuning overhead being offloaded to the test server.</span></span> <span data-ttu-id="305b5-147">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 튜닝 관리자가 이 XML 입력 파일을 사용하여 튜닝 권장 사항을 생성할 때는 분할에 대해 고려하거나`<FeatureSet>IDX</FeatureSet>`의 기존 물리적 디자인 구조를 유지할 필요 없이 인덱스( `MyDatabaseName`)만 고려하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="305b5-147">When [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Tuning Advisor generates its tuning recommendation using this XML input file, it should consider indexes only (`<FeatureSet>IDX</FeatureSet>`), no partitioning, and need not keep any of the existing physical design structures in `MyDatabaseName`.</span></span>

```
<?xml version="1.0" encoding="utf-16" ?>
<DTAXML xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="https://schemas.microsoft.com/sqlserver/2004/07/dta">
  <DTAInput>
    <Server>
      <Name>MyServerName</Name>
      <Database>
        <Name>MyDatabaseName</Name>
      </Database>
    </Server>
    <Workload>
      <File>MyWorkloadScript.sql</File>
    </Workload>
    <TuningOptions>
      <TestServer>MyTestServerName</TestServer>
      <FeatureSet>IDX</FeatureSet>
      <Partitioning>NONE</Partitioning>
      <KeepExisting>NONE</KeepExisting>
    </TuningOptions>
  </DTAInput>
</DTAXML>
```

## <a name="see-also"></a><span data-ttu-id="305b5-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="305b5-148">See Also</span></span>
 <span data-ttu-id="305b5-149">[테스트 서버 사용 시 고려 사항](considerations-for-using-test-servers.md) [XML 입력 파일 참조 &#40;데이터베이스 엔진 튜닝 관리자&#41;](database-engine-tuning-advisor.md)</span><span class="sxs-lookup"><span data-stu-id="305b5-149">[Considerations for Using Test Servers](considerations-for-using-test-servers.md) [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](database-engine-tuning-advisor.md)</span></span>


