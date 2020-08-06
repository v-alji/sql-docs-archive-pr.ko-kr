---
title: SQL Server 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine analysis [Upgrade Advisor]
- SQL Server Upgrade Advisor, Database Engine
- Upgrade Advisor [SQL Server], Database Engine
- analyzing system [Upgrade Advisor], Database Engine
ms.assetid: 44a18bfe-e593-47a5-995f-382c01d3f618
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2b885e7616506fd08cae99166cc794dbfb5dac7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735847"
---
# <a name="sql-server-parameters"></a><span data-ttu-id="4a122-102">SQL Server 매개 변수</span><span class="sxs-lookup"><span data-stu-id="4a122-102">SQL Server Parameters</span></span>
  <span data-ttu-id="4a122-103">이 페이지에서는 분석기가 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 분석에 사용할 매개 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-103">On this page, set parameters that the analyzer will use for [!INCLUDE[ssDE](../../includes/ssde-md.md)] analysis.</span></span> <span data-ttu-id="4a122-104">데이터베이스 하나, 여러 개 또는 모두를 분석하고, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 만든 추적 파일을 분석하며, SQL 배치 파일을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-104">You can analyze one, several, or all databases, analyze trace files that were created by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], and analyze SQL batch files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a122-105">추적 파일이나 SQL 배치 파일을 분석하기 위해 전송할 경우에만 일부 업그레이드 문제가 감지될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-105">Some upgrade issues can be detected only if you submit trace files or SQL batch files to be analyzed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4a122-106">옵션</span><span class="sxs-lookup"><span data-stu-id="4a122-106">Options</span></span>  
 <span data-ttu-id="4a122-107">**분석할 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="4a122-107">**Database(s) to analyze**</span></span>  
 <span data-ttu-id="4a122-108">모든 데이터베이스를 분석 하려면 **모든 데이터베이스** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-108">To analyze all databases, select the **All databases** check box.</span></span> <span data-ttu-id="4a122-109">일부 데이터베이스를 분석하려면 분석할 각 데이터베이스 옆에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-109">To analyze a selection of databases, select the check box next to each database to include in the scan.</span></span>  
  
 <span data-ttu-id="4a122-110">**추적 파일 분석**</span><span class="sxs-lookup"><span data-stu-id="4a122-110">**Analyze trace file(s)**</span></span>  
 <span data-ttu-id="4a122-111">파일 시스템에 있는 추적 파일을 분석하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-111">Select this check box to analyze trace files in the file system.</span></span>  
  
 <span data-ttu-id="4a122-112">**추적 파일의 경로**</span><span class="sxs-lookup"><span data-stu-id="4a122-112">**Path to trace file(s)**</span></span>  
 <span data-ttu-id="4a122-113">하나 이상의 파일을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-113">You can analyze one or more files.</span></span> <span data-ttu-id="4a122-114">위치를 찾아 여러 개의 파일을 선택하거나 파일 이름을 여러 개 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-114">You can browse to a location and select multiple files, or you can provide multiple file names.</span></span> <span data-ttu-id="4a122-115">각 파일의 전체 경로 이름(파일 이름 포함)을 사용하고 파이프 문자(|)로 각 항목을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-115">Use the full path name to each file, include the file name, and separate entries by using the pipe character (|).</span></span>  
  
 <span data-ttu-id="4a122-116">**추적 파일 분석**을 사용 하도록 설정 하는 경우 경로 이름과 파일 이름을 입력할 때까지 **다음** 을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-116">If you enable **Analyze trace file(s)**, **Next** is disabled until you enter a path name and a file name.</span></span>  
  
 <span data-ttu-id="4a122-117">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]배치 파일 분석**</span><span class="sxs-lookup"><span data-stu-id="4a122-117">**Analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch file(s)**</span></span>  
 <span data-ttu-id="4a122-118">파일 시스템에 있는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 배치 파일을 분석하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-118">Select this check box to analyze [!INCLUDE[tsql](../../includes/tsql-md.md)] batch files in the file system.</span></span>  
  
 <span data-ttu-id="4a122-119">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]배치 파일의 경로**</span><span class="sxs-lookup"><span data-stu-id="4a122-119">**Path to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch file(s)**</span></span>  
 <span data-ttu-id="4a122-120">하나 이상의 배치 파일을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-120">You can analyze one or more batch files.</span></span> <span data-ttu-id="4a122-121">위치를 찾아 여러 개의 파일을 선택하거나 파일 이름을 여러 개 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-121">You can browse to a location and select multiple files, or you can type multiple file names.</span></span> <span data-ttu-id="4a122-122">각 파일의 전체 경로 이름(파일 이름 포함)을 사용하고 파이프 문자(|)로 각 항목을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-122">Use the full path name to each file, include the file name, and separate entries by using the pipe character (|).</span></span>  
  
 <span data-ttu-id="4a122-123">**SQL 배치 파일 분석**을 사용 하도록 설정 하는 경우 경로 이름과 파일 이름을 입력할 때까지 **다음** 단추를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-123">If you enable **Analyze SQL batch file(s)**, the **Next** button is disabled until you enter a path name and a file name.</span></span>  
  
 <span data-ttu-id="4a122-124">**SQL 일괄 처리 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="4a122-124">**SQL Batch Separator**</span></span>  
 <span data-ttu-id="4a122-125">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문의 일괄 처리를 구분하는 데 사용되는 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-125">The text that is used to separate batches of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="4a122-126">기본값은 **GO**입니다.</span><span class="sxs-lookup"><span data-stu-id="4a122-126">The default value is **GO**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a122-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a122-127">See Also</span></span>  
 <span data-ttu-id="4a122-128">[업그레이드 관리자 작업](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="4a122-128">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="4a122-129">업그레이드 관리자 사용자 인터페이스 참조</span><span class="sxs-lookup"><span data-stu-id="4a122-129">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
