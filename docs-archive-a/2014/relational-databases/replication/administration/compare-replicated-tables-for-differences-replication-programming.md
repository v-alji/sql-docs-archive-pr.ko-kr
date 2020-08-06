---
title: 복제된 테이블의 차이점 비교(복제 프로그래밍) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- tablediff utility
- comparing replicated tables
ms.assetid: cd253a17-0c85-42b4-912c-690169ebe799
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d804c7d4ac9cc54fa144b7054c6032663b76c0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741903"
---
# <a name="compare-replicated-tables-for-differences-replication-programming"></a><span data-ttu-id="35f69-102">복제된 테이블의 차이점 비교(복제 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="35f69-102">Compare Replicated Tables for Differences (Replication Programming)</span></span>
  <span data-ttu-id="35f69-103">아티클 유효성 검사는 게시자 및 구독자에서 테이블 아티클의 게시된 데이터가 일치하지 않는지 여부를 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-103">Article validation is used to determine if published data for table articles at the Publisher and Subscriber are not identical, which can indicate non-convergence.</span></span> <span data-ttu-id="35f69-104">자세한 내용은 [복제된 데이터의 유효성 검사](../validate-data-at-the-subscriber.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35f69-104">For more information, see [Validate Replicated Data](../validate-data-at-the-subscriber.md).</span></span> <span data-ttu-id="35f69-105">그러나 유효성 검사를 통해서는 성공 또는 실패 정보만 반환되고 원본 테이블과 대상 테이블의 차이점에 대한 정보는 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-105">However, validation only returns pass or fail information and does not provide any information about what is different between the source and destination tables.</span></span> <span data-ttu-id="35f69-106">**tablediff** 명령 프롬프트 유틸리티는 두 테이블 간의 세부 차이점 정보를 반환하며 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 스크립트를 생성하여 구독이 게시자의 데이터와 일치하게 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-106">The **tablediff** command prompt utility returns detailed difference information between two tables and can even generate a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script to bring a subscription into convergence with data at the Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35f69-107">**tablediff** 유틸리티는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서버에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-107">The **tablediff** utility is only supported for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] servers.</span></span>  
  
### <a name="to-compare-replicated-tables-for-differences-using-tablediff"></a><span data-ttu-id="35f69-108">tablediff를 사용하여 복제된 테이블의 차이점을 비교하려면</span><span class="sxs-lookup"><span data-stu-id="35f69-108">To compare replicated tables for differences using tablediff</span></span>  
  
1.  <span data-ttu-id="35f69-109">복제 토폴로지에 있는 서버의 명령 프롬프트에서 [tablediff Utility](../../../tools/tablediff-utility.md)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-109">From the command prompt at any server in a replication topology, run the [tablediff Utility](../../../tools/tablediff-utility.md).</span></span> <span data-ttu-id="35f69-110">다음 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-110">Specify the following parameters:</span></span>  
  
    -   <span data-ttu-id="35f69-111">**-sourceserver** - 올바른 데이터가 있는 서버(대개 게시자)의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-111">**-sourceserver** - name of the server on which the data is known to be correct, usually the Publisher.</span></span>  
  
    -   <span data-ttu-id="35f69-112">**-sourcedatabase** - 올바른 데이터가 들어 있는 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-112">**-sourcedatabase** - name of the database containing the correct data.</span></span>  
  
    -   <span data-ttu-id="35f69-113">**-sourcetable** - 비교할 아티클의 원본 테이블 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-113">**-sourcetable** - name of the source table for the article being compared.</span></span>  
  
    -   <span data-ttu-id="35f69-114">**-sourceschema** (옵션) - 원본 테이블의 스키마 소유자입니다(기본 스키마가 아닌 경우).</span><span class="sxs-lookup"><span data-stu-id="35f69-114">(Optional) **-sourceschema** - schema owner of the source table, if not the default schema.</span></span>  
  
    -   <span data-ttu-id="35f69-115">**-sourceuser** 및 **-sourcepassword** (옵션) - SQL Server 인증을 사용하여 게시자에 연결할 경우에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-115">(Optional) **-sourceuser** and **-sourcepassword** when using SQL Server Authentication to connect to the Publisher.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="35f69-116">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="35f69-116">When possible, use Windows Authentication.</span></span> <span data-ttu-id="35f69-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용해야 하는 경우에는 런타임에 사용자에게 보안 자격 증명을 지정하라는 메시지가 표시되도록 하십시오.</span><span class="sxs-lookup"><span data-stu-id="35f69-117">If you must use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="35f69-118">자격 증명을 스크립트 파일에 저장해야 하는 경우에는 파일에 무단으로 액세스하지 못하도록 보안을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-118">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
    -   <span data-ttu-id="35f69-119">**-destinationserver** - 데이터를 비교할 서버(대개 구독자)의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-119">**-destinationserver** - name of the server on which the data is being compared, usually a Subscriber.</span></span>  
  
    -   <span data-ttu-id="35f69-120">**-destinationdatabase** - 비교할 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-120">**-destinationdatabase** - name of a the database being compared.</span></span>  
  
    -   <span data-ttu-id="35f69-121">**-destinationtable** - 비교할 테이블의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-121">**-destinationtable** - name of the table being compared.</span></span>  
  
    -   <span data-ttu-id="35f69-122">**-destinationschema** (옵션) - 대상 테이블의 스키마 소유자입니다(기본 스키마가 아닌 경우).</span><span class="sxs-lookup"><span data-stu-id="35f69-122">(Optional) **-destinationschema** - schema owner of the destination table, if not the default schema.</span></span>  
  
    -   <span data-ttu-id="35f69-123">**-destinationuser** 및 **-destinationpassword** (옵션) - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하여 구독자에 연결할 경우에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-123">(Optional) **-destinationuser** and **-destinationpassword** when using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication to connect to the Subscriber.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="35f69-124">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="35f69-124">When possible, use Windows Authentication.</span></span> <span data-ttu-id="35f69-125">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용해야 하는 경우에는 런타임에 사용자에게 보안 자격 증명을 지정하라는 메시지가 표시되도록 하십시오.</span><span class="sxs-lookup"><span data-stu-id="35f69-125">If you must use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="35f69-126">자격 증명을 스크립트 파일에 저장해야 하는 경우에는 파일에 무단으로 액세스하지 못하도록 보안을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-126">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
    -   <span data-ttu-id="35f69-127">**-c** (옵션) - 열 수준 비교를 수행하려는 경우에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-127">(Optional) Use **-c** to do a column-level comparison.</span></span>  
  
    -   <span data-ttu-id="35f69-128">**-q** (옵션) - 행 개수 전용 및 스키마 전용 비교를 수행하려는 경우에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-128">(Optional) Use **-q** to do a fast, row count- and schema-only comparison.</span></span>  
  
    -   <span data-ttu-id="35f69-129">**-o** (옵션) - 결과를 파일로 출력하려면 이 매개 변수에 파일 이름 및 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-129">(Optional) Specify a file name and path for **-o** to output the results to a file.</span></span>  
  
    -   <span data-ttu-id="35f69-130">**-et**(옵션) - 결과를 삽입할 구독 데이터베이스의 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-130">(Optional) Specify a table in the subscription database into which to insert results for **-et**.</span></span> <span data-ttu-id="35f69-131">해당 테이블이 이미 있는 경우 **-dt** 를 지정하여 먼저 해당 테이블을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-131">If the table already exists, specify **-dt** to first drop the table.</span></span>  
  
    -   <span data-ttu-id="35f69-132">**-f** (옵션) - 구독자의 데이터를 게시자의 데이터와 일치하게 수정하려면 이 매개 변수를 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-132">(Optional) Use **-f** to generate a [!INCLUDE[tsql](../../../includes/tsql-md.md)] file to fix data at the Subscriber so that it matches data at the Publisher.</span></span> <span data-ttu-id="35f69-133">각 파일의 **문 수를 지정하려면** -df [!INCLUDE[tsql](../../../includes/tsql-md.md)] 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-133">Use **-df** to specify the number of [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements in each file.</span></span>  
  
    -   <span data-ttu-id="35f69-134">**-rc** 및 **-ri** (옵션) - 작업을 다시 시도할 횟수와 다시 시도 간격을 지정하려는 경우에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-134">(Optional) Use **-rc** and **-ri** to specify the number of times to retry an operation and the retry interval.</span></span>  
  
    -   <span data-ttu-id="35f69-135">**-strict** (옵션) - 원본 테이블과 대상 테이블 간의 엄격한 스키마 비교를 적용하려는 경우에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="35f69-135">(Optional) Use **-strict** to enforce strict schema comparison between source and destination tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35f69-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="35f69-136">See Also</span></span>  
 [<span data-ttu-id="35f69-137">구독자에서 데이터 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="35f69-137">Validate Data at the Subscriber</span></span>](../validate-data-at-the-subscriber.md)  
  
  
