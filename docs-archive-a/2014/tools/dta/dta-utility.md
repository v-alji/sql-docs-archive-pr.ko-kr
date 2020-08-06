---
title: dta 유틸리티 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- physical design structures [SQL Server]
- command prompt utilities [SQL Server], dta
- dta utility
- tuning databases [SQL Server], Database Engine Tuning Advisor
- workloads [SQL Server], analyzing
- dta utility, about dta utility
- performance [SQL Server], Database Engine Tuning Advisor
- Database Engine Tuning Advisor [SQL Server], command prompt
- optimizing databases [SQL Server]
ms.assetid: a0b210ce-9b58-4709-80cb-9363b68a1f5a
author: stevestein
ms.author: sstein
ms.openlocfilehash: f9cd5a904993f1044c1cbeff8e1cdfc07332da64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740612"
---
# <a name="dta-utility"></a><span data-ttu-id="803b8-102">dta 유틸리티</span><span class="sxs-lookup"><span data-stu-id="803b8-102">dta Utility</span></span>
  <span data-ttu-id="803b8-103">**dta** 유틸리티는 데이터베이스 엔진 튜닝 관리자의 명령 프롬프트 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-103">The **dta** utility is the command prompt version of Database Engine Tuning Advisor.</span></span> <span data-ttu-id="803b8-104">**dta** 유틸리티를 통해 애플리케이션과 스크립트에서 데이터베이스 엔진 튜닝 관리자의 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-104">The **dta** utility is designed to allow you to use Database Engine Tuning Advisor functionality in applications and scripts.</span></span>  
  
 <span data-ttu-id="803b8-105">데이터베이스 엔진 튜닝 관리자와 마찬가지로 **dta** 유틸리티는 작업을 분석하고 이 작업에 대해 서버 성능을 향상시키기 위한 물리적 디자인 구조를 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-105">Like Database Engine Tuning Advisor, the **dta** utility analyzes a workload and recommends physical design structures to improve server performance for that workload.</span></span> <span data-ttu-id="803b8-106">작업은 계획 캐시, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 추적 파일이나 테이블 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-106">The workload can be a plan cache, a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace file or table, or a [!INCLUDE[tsql](../../includes/tsql-md.md)] script.</span></span> <span data-ttu-id="803b8-107">물리적 디자인 구조에는 인덱스, 인덱싱된 뷰 및 분할이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-107">Physical design structures include indexes, indexed views, and partitioning.</span></span> <span data-ttu-id="803b8-108">작업을 분석한 후 **dta** 유틸리티는 실제 데이터베이스 디자인을 제안하며 이 제안 사항을 구현하는 데 필요한 스크립트를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-108">After analyzing a workload, the **dta** utility produces a recommendation for the physical design of databases and can generate the necessary script to implement the recommendation.</span></span> <span data-ttu-id="803b8-109">명령 프롬프트에서 **-if** 또는 **-it** 인수를 사용하여 작업을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-109">Workloads can be specified from the command prompt with the **-if** or the **-it** argument.</span></span> <span data-ttu-id="803b8-110">또한 명령 프롬프트에서 **-ix** 인수를 사용하여 XML 입력 파일을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-110">You can also specify an XML input file from the command prompt with the **-ix** argument.</span></span> <span data-ttu-id="803b8-111">이러한 경우 작업은 XML 입력 파일에서 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-111">In that case, the workload is specified in the XML input file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="803b8-112">구문</span><span class="sxs-lookup"><span data-stu-id="803b8-112">Syntax</span></span>  
  
```  
  
      dta  
[ -? ] |  
[  
      [ -S server_name[ \instance ] ]  
      { { -U login_id [-P password ] } | -E  }  
      { -D database_name [ ,...n ] }  
      [ -ddatabase_name ]   
      [ -Tltable_list | -Tf table_list_file ]  
      { -if workload_file | -it workload_trace_table_name  |   
        -ip | -ipf }  
      { -ssession_name | -IDsession_ID }  
      [ -F ]  
      [ -of output_script_file_name ]  
      [ -oroutput_xml_report_file_name ]  
      [ -ox output_XML_file_name ]  
      [ -rl analysis_report_list [ ,...n ] ]  
      [ -ix input_XML_file_name ]  
      [ -A time_for_tuning_in_minutes ]  
      [ -nnumber_of_events ]  
      [ -m minimum_improvement ]  
      [ -fa physical_design_structures_to_add ]  
      [ -fi ]  
      [ -fppartitioning_strategy ]  
      [ -fk keep_existing_option ]  
      [ -fxdrop_only_mode ]  
      [ -B storage_size ]  
      [ -cmax_key_columns_in_index ]  
      [ -C max_columns_in_index ]  
      [ -e | -e tuning_log_name ]  
      [ -N online_option]  
      [ -q ]  
      [ -u ]  
      [ -x ]  
      [ -a ]  
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="803b8-113">인수</span><span class="sxs-lookup"><span data-stu-id="803b8-113">Arguments</span></span>  
 <span data-ttu-id="803b8-114">**-?**</span><span class="sxs-lookup"><span data-stu-id="803b8-114">**-?**</span></span>  
 <span data-ttu-id="803b8-115">사용 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-115">Displays usage information.</span></span>  
  
 <span data-ttu-id="803b8-116">**-A** _time_for_tuning_in_minutes_</span><span class="sxs-lookup"><span data-stu-id="803b8-116">**-A** _time_for_tuning_in_minutes_</span></span>  
 <span data-ttu-id="803b8-117">튜닝 시간 제한(분)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-117">Specifies the tuning time limit in minutes.</span></span> <span data-ttu-id="803b8-118">**dta** 는 지정된 시간 동안 작업을 튜닝하고 제안된 실제 디자인 변경 내용을 사용하여 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-118">**dta** uses the specified amount of time to tune the workload and generate a script with the recommended physical design changes.</span></span> <span data-ttu-id="803b8-119">**dta** 의 기본 튜닝 시간은 8시간입니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-119">By default **dta** assumes a tuning time of 8 hours.</span></span> <span data-ttu-id="803b8-120">0을 지정하면 튜닝에 시간 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-120">Specifying 0allows unlimited tuning time.</span></span> <span data-ttu-id="803b8-121">**dta** 는 시간 제한이 만료되기 전에 전체 작업 튜닝을 마칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-121">**dta** might finish tuning the entire workload before the time limit expires.</span></span> <span data-ttu-id="803b8-122">그러나 전체 작업이 튜닝되도록 하려면 무제한 튜닝 시간(-A 0)을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-122">However, to make sure that the entire workload is tuned, we recommend that you specify unlimited tuning time (-A 0).</span></span>  
  
 <span data-ttu-id="803b8-123">**-a**</span><span class="sxs-lookup"><span data-stu-id="803b8-123">**-a**</span></span>  
 <span data-ttu-id="803b8-124">작업을 튜닝한 후 사용자에게 메시지를 표시하지 않고 제안 사항을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-124">Tunes workload and applies the recommendation without prompting you.</span></span>  
  
 <span data-ttu-id="803b8-125">**-B** _storage_size_</span><span class="sxs-lookup"><span data-stu-id="803b8-125">**-B** _storage_size_</span></span>  
 <span data-ttu-id="803b8-126">권장되는 인덱스 및 분할에서 소비할 수 있는 최대 공간(MB)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-126">Specifies the maximum space in megabytes that can be consumed by the recommended index and partitioning.</span></span> <span data-ttu-id="803b8-127">여러 개의 데이터베이스를 튜닝할 경우 모든 데이터베이스에 대한 권장 구성은 공간 계산을 고려하여 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-127">When multiple databases are tuned, recommendations for all databases are considered for the space calculation.</span></span> <span data-ttu-id="803b8-128">기본적으로 **dta** 는 다음 스토리지 크기 중 더 작은 크기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-128">By default, **dta** assumes the smaller of the following storage sizes:</span></span>  
  
-   <span data-ttu-id="803b8-129">현재 원시 데이터 크기의 3배이며 데이터베이스의 테이블에 있는 힙과 클러스터형 인덱스의 전체 크기를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-129">Three times the current raw data size, which includes the total size of heaps and clustered indexes on tables in the database.</span></span>  
  
-   <span data-ttu-id="803b8-130">연결된 모든 디스크 드라이브의 여유 공간과 원시 데이터 크기를 더한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-130">The free space on all attached disk drives plus the raw data size.</span></span>  
  
 <span data-ttu-id="803b8-131">기본 스토리지 크기는 비클러스터형 인덱스 및 인덱싱된 뷰를 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-131">The default storage size does not include nonclustered indexes and indexed views.</span></span>  
  
 <span data-ttu-id="803b8-132">**-C** _max_columns_in_index_</span><span class="sxs-lookup"><span data-stu-id="803b8-132">**-C** _max_columns_in_index_</span></span>  
 <span data-ttu-id="803b8-133">**dta** 에서 제안하는 인덱스의 최대 열 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-133">Specifies the maximum number of columns in indexes that **dta** proposes.</span></span> <span data-ttu-id="803b8-134">최대값은 1024입니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-134">The maximum value  is 1024.</span></span> <span data-ttu-id="803b8-135">기본적으로 이 인수는 16으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-135">By default, this argument is set to 16.</span></span>  
  
 <span data-ttu-id="803b8-136">**-c** _max_key_columns_in_index_</span><span class="sxs-lookup"><span data-stu-id="803b8-136">**-c** _max_key_columns_in_index_</span></span>  
 <span data-ttu-id="803b8-137">**dta** 에서 제안하는 인덱스의 최대 키 열 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-137">Specifies the maximum number of key columns in indexes that **dta** proposes.</span></span> <span data-ttu-id="803b8-138">기본값은 16이며 허용되는 최대값입니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-138">The default value is 16, the maximum value allowed.</span></span> <span data-ttu-id="803b8-139">**dta** 는 포함된 열을 사용하여 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-139">**dta** also considers creating indexes with included columns.</span></span> <span data-ttu-id="803b8-140">포함된 열을 사용할 때 권장되는 인덱스는 이 인수에 지정된 열 수를 초과할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-140">Indexes recommended with included columns may exceed the number of columns specified in this argument.</span></span>  
  
 <span data-ttu-id="803b8-141">**-D** _database_name_</span><span class="sxs-lookup"><span data-stu-id="803b8-141">**-D** _database_name_</span></span>  
 <span data-ttu-id="803b8-142">튜닝할 각 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-142">Specifies the name of each database that is to be tuned.</span></span> <span data-ttu-id="803b8-143">첫 번째 데이터베이스가 기본 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-143">The first database is the default database.</span></span> <span data-ttu-id="803b8-144">다음과 같이 데이터베이스 이름을 쉼표로 구분하여 여러 데이터베이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-144">You can specify multiple databases by separating the database names with commas, for example:</span></span>  
  
```  
dta -D database_name1, database_name2...  
```  
  
 <span data-ttu-id="803b8-145">또는 다음과 같이 각 데이터베이스 이름에 **–D** 인수를 사용하여 여러 데이터베이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-145">Alternatively, you can specify multiple databases by using the **-D** argument for each database name, for example:</span></span>  
  
```  
dta -D database_name1 -D database_name2... n  
```  
  
 <span data-ttu-id="803b8-146">**-D** 인수는 필수 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-146">The **-D** argument is mandatory.</span></span> <span data-ttu-id="803b8-147">**-d** 인수를 지정하지 않은 경우 초기에 **dta** 는 작업에서 첫 번째 `USE database_name` 절로 지정된 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-147">If the **-d** argument has not been specified, **dta** initially connects to the database that is specified with the first `USE database_name` clause in the workload.</span></span> <span data-ttu-id="803b8-148">작업에 명시적 `USE database_name` 절이 없으면 **-d** 인수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-148">If there is not explicit `USE database_name` clause in the workload, you must use the **-d** argument.</span></span>  
  
 <span data-ttu-id="803b8-149">예를 들어 작업에 명시적 `USE database_name` 절이 포함되지 않은 경우 다음 **dta** 명령을 사용하면 권장 구성이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-149">For example, if you have a workload that contains no explicit `USE database_name` clause, and you use the following **dta** command, a recommendation will not be generated:</span></span>  
  
```  
dta -D db_name1, db_name2...  
```  
  
 <span data-ttu-id="803b8-150">그러나 같은 작업에서 **-d** 인수를 사용하는 다음 **dta** 명령을 사용하면 권장 구성이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-150">But if you use the same workload, and use the following **dta** command that uses the **-d** argument, a recommendation will be generated:</span></span>  
  
```  
dta -D db_name1, db_name2 -d db_name1  
```  
  
 <span data-ttu-id="803b8-151">**-d** _database_name_</span><span class="sxs-lookup"><span data-stu-id="803b8-151">**-d** _database_name_</span></span>  
 <span data-ttu-id="803b8-152">작업을 튜닝할 때 **dta** 가 연결하는 첫 번째 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-152">Specifies the first database to which **dta** connects when tuning a workload.</span></span> <span data-ttu-id="803b8-153">이 인수에는 데이터베이스를 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-153">Only one database can be specified for this argument.</span></span> <span data-ttu-id="803b8-154">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-154">For example:</span></span>  
  
```  
dta -d AdventureWorks2012 ...  
```  
  
 <span data-ttu-id="803b8-155">데이터베이스 이름을 여러 개 지정할 경우 **dta** 는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-155">If multiple database names are specified, then **dta** returns an error.</span></span> <span data-ttu-id="803b8-156">**-d** 인수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-156">The **-d** argument is optional.</span></span>  
  
 <span data-ttu-id="803b8-157">XML 입력 파일을 사용 하는 경우 요소 아래에 있는 요소를 사용 하 여 **dta** 가 연결 하는 첫 번째 데이터베이스를 지정할 수 있습니다 `DatabaseToConnect` `TuningOptions` .</span><span class="sxs-lookup"><span data-stu-id="803b8-157">If you are using an XML input file, you can specify the first database to which **dta** connects by using the `DatabaseToConnect` element that is located under the `TuningOptions` element.</span></span> <span data-ttu-id="803b8-158">자세한 내용은 [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="803b8-158">For more information, see [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).</span></span>  
  
 <span data-ttu-id="803b8-159">데이터베이스를 하나만 튜닝하는 경우 **-d** 인수는 **sqlcmd** 유틸리티의 **-d** 인수와 유사한 기능을 제공하지만 USE *database_name* 문을 실행하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-159">If you are tuning only one database, the **-d** argument provides functionality that is similar to the **-d** argument in the **sqlcmd** utility, but it does not execute the USE *database_name* statement.</span></span> <span data-ttu-id="803b8-160">자세한 내용은 [sqlcmd Utility](../sqlcmd-utility.md)을(를) 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="803b8-160">For more information, see [sqlcmd Utility](../sqlcmd-utility.md).</span></span>  
  
 <span data-ttu-id="803b8-161">**-E**</span><span class="sxs-lookup"><span data-stu-id="803b8-161">**-E**</span></span>  
 <span data-ttu-id="803b8-162">암호를 요구하지 않고 트러스트된 연결을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-162">Uses a trusted connection instead of requesting a password.</span></span> <span data-ttu-id="803b8-163">로그인 ID를 지정하는 **-E** 인수 또는 **-U** 인수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-163">Either the **-E** argument or the **-U** argument, which specifies a login ID, must be used.</span></span>  
  
 <span data-ttu-id="803b8-164">**-e** _tuning_log_name_</span><span class="sxs-lookup"><span data-stu-id="803b8-164">**-e** _tuning_log_name_</span></span>  
 <span data-ttu-id="803b8-165">**dta** 가 튜닝할 수 없는 이벤트를 기록하는 테이블 또는 파일의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-165">Specifies the name of the table or file where **dta** records events that it could not tune.</span></span> <span data-ttu-id="803b8-166">이 테이블은 튜닝을 수행하는 서버에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-166">The table is created on the server where the tuning is performed.</span></span>  
  
 <span data-ttu-id="803b8-167">테이블을 사용하는 경우 *[database_name].[owner_name].table_name*형식으로 해당 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-167">If a table is used, specify its name in the format: *[database_name].[owner_name].table_name*.</span></span> <span data-ttu-id="803b8-168">다음 표에서는 각 매개 변수의 기본값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-168">The following table shows the default values for each parameter:</span></span>  
  
|<span data-ttu-id="803b8-169">매개 변수</span><span class="sxs-lookup"><span data-stu-id="803b8-169">Parameter</span></span>|<span data-ttu-id="803b8-170">기본값</span><span class="sxs-lookup"><span data-stu-id="803b8-170">Default value</span></span>|  
|---------------|-------------------|  
|<span data-ttu-id="803b8-171">*database_name*</span><span class="sxs-lookup"><span data-stu-id="803b8-171">*database_name*</span></span>|<span data-ttu-id="803b8-172">*–D* 옵션으로 지정된 **database_name**</span><span class="sxs-lookup"><span data-stu-id="803b8-172">*database_name* specified with the **-D** option</span></span>|  
|<span data-ttu-id="803b8-173">*owner_name*</span><span class="sxs-lookup"><span data-stu-id="803b8-173">*owner_name*</span></span>|<span data-ttu-id="803b8-174">**dbo**</span><span class="sxs-lookup"><span data-stu-id="803b8-174">**dbo**</span></span><br /><br /> <span data-ttu-id="803b8-175">참고: *owner_name* 은 **dbo**여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-175">Note: *owner_name* must be **dbo**.</span></span> <span data-ttu-id="803b8-176">다른 값을 지정할 경우 **dta** 를 실행할 수 없으며 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-176">If any other value is specified, then **dta** execution fails and it returns an error.</span></span>|  
|<span data-ttu-id="803b8-177">*table_name*</span><span class="sxs-lookup"><span data-stu-id="803b8-177">*table_name*</span></span>|<span data-ttu-id="803b8-178">None</span><span class="sxs-lookup"><span data-stu-id="803b8-178">None</span></span>|  
  
 <span data-ttu-id="803b8-179">파일을 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="803b8-179">If a file is used, specify .xml as its extension.</span></span> <span data-ttu-id="803b8-180">TuningLog.xml과 같이 확장명으로 .xml을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-180">For example, TuningLog.xml.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="803b8-181">**dta** 유틸리티는 세션을 삭제해도 사용자 지정 튜닝 로그 테이블의 내용을 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-181">The **dta** utility does not delete the contents of user-specified tuning log tables if the session is deleted.</span></span> <span data-ttu-id="803b8-182">매우 큰 작업을 튜닝하는 경우 튜닝 로그에 대해 테이블을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-182">When tuning very large workloads, we recommend that a table be specified for the tuning log.</span></span> <span data-ttu-id="803b8-183">큰 작업을 튜닝하면 큰 튜닝 로그가 생성되기 때문에 테이블을 사용하면 세션을 보다 빨리 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-183">Since tuning large workloads can result in large tuning logs, the sessions can be deleted much faster when a table is used.</span></span>  
  
 <span data-ttu-id="803b8-184">**-F**</span><span class="sxs-lookup"><span data-stu-id="803b8-184">**-F**</span></span>  
 <span data-ttu-id="803b8-185">**dta** 가 기존의 출력 파일을 덮어쓰도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-185">Permits **dta** to overwrite an existing output file.</span></span> <span data-ttu-id="803b8-186">이름이 같은 출력 파일이 이미 있을 경우 **-F** 를 지정하지 않으면 **dta**는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-186">If an output file with the same name already exists and **-F** is not specified, **dta**returns an error.</span></span> <span data-ttu-id="803b8-187">**-of** , **-or**또는 **-ox**와 함께 **-F**를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-187">You can use **-F** with **-of**, **-or**, or **-ox**.</span></span>  
  
 <span data-ttu-id="803b8-188">**-fa** _physical_design_structures_to_add_</span><span class="sxs-lookup"><span data-stu-id="803b8-188">**-fa** _physical_design_structures_to_add_</span></span>  
 <span data-ttu-id="803b8-189">**dta** 가 권장 구성에 포함해야 할 실제 디자인 구조 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-189">Specifies what types of physical design structures **dta** should include in the recommendation.</span></span> <span data-ttu-id="803b8-190">다음 표에서는 이 인수에 지정할 수 있는 값을 나열하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-190">The following table lists and describes the values that can be specified for this argument.</span></span> <span data-ttu-id="803b8-191">값을 지정 하지 않으면 **dta** 는 기본 **-fa**를 사용 `IDX` 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-191">When no value is specified, **dta** uses the default **-fa**`IDX`.</span></span>  
  
|<span data-ttu-id="803b8-192">값</span><span class="sxs-lookup"><span data-stu-id="803b8-192">Value</span></span>|<span data-ttu-id="803b8-193">Description</span><span class="sxs-lookup"><span data-stu-id="803b8-193">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="803b8-194">IDX_IV</span><span class="sxs-lookup"><span data-stu-id="803b8-194">IDX_IV</span></span>|<span data-ttu-id="803b8-195">인덱스와 인덱싱된 뷰</span><span class="sxs-lookup"><span data-stu-id="803b8-195">Indexes and indexed views.</span></span>|  
|<span data-ttu-id="803b8-196">IDX</span><span class="sxs-lookup"><span data-stu-id="803b8-196">IDX</span></span>|<span data-ttu-id="803b8-197">인덱스만</span><span class="sxs-lookup"><span data-stu-id="803b8-197">Indexes only.</span></span>|  
|<span data-ttu-id="803b8-198">IV</span><span class="sxs-lookup"><span data-stu-id="803b8-198">IV</span></span>|<span data-ttu-id="803b8-199">인덱싱된 뷰만</span><span class="sxs-lookup"><span data-stu-id="803b8-199">Indexed views only.</span></span>|  
|<span data-ttu-id="803b8-200">NCL_IDX</span><span class="sxs-lookup"><span data-stu-id="803b8-200">NCL_IDX</span></span>|<span data-ttu-id="803b8-201">비클러스터형 인덱스만</span><span class="sxs-lookup"><span data-stu-id="803b8-201">Nonclustered indexes only.</span></span>|  
  
 <span data-ttu-id="803b8-202">**-fi**</span><span class="sxs-lookup"><span data-stu-id="803b8-202">**-fi**</span></span>  
 <span data-ttu-id="803b8-203">필터링된 인덱스가 새 제안 사항을 만들 때 고려되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-203">Specifies that filtered indexes be considered for new recommendations.</span></span> <span data-ttu-id="803b8-204">자세한 내용은 [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="803b8-204">For more information, see [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md).</span></span>  
  
 <span data-ttu-id="803b8-205">**-fk** _keep_existing_option_</span><span class="sxs-lookup"><span data-stu-id="803b8-205">**-fk** _keep_existing_option_</span></span>  
 <span data-ttu-id="803b8-206">권장 구성을 생성할 때 **dta** 가 유지해야 할 기존의 실제 디자인 구조를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-206">Specifies what existing physical design structures **dta** must retain when generating its recommendation.</span></span> <span data-ttu-id="803b8-207">다음 표에서는 이 인수에 지정할 수 있는 값을 나열하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-207">The following table lists and describes the values that can be specified for this argument:</span></span>  
  
|<span data-ttu-id="803b8-208">값</span><span class="sxs-lookup"><span data-stu-id="803b8-208">Value</span></span>|<span data-ttu-id="803b8-209">Description</span><span class="sxs-lookup"><span data-stu-id="803b8-209">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="803b8-210">없음</span><span class="sxs-lookup"><span data-stu-id="803b8-210">NONE</span></span>|<span data-ttu-id="803b8-211">기존 구조 없음</span><span class="sxs-lookup"><span data-stu-id="803b8-211">No existing structures</span></span>|  
|<span data-ttu-id="803b8-212">ALL</span><span class="sxs-lookup"><span data-stu-id="803b8-212">ALL</span></span>|<span data-ttu-id="803b8-213">기존의 모든 구조</span><span class="sxs-lookup"><span data-stu-id="803b8-213">All existing structures</span></span>|  
|<span data-ttu-id="803b8-214">ALIGNED</span><span class="sxs-lookup"><span data-stu-id="803b8-214">ALIGNED</span></span>|<span data-ttu-id="803b8-215">모든 파티션 정렬 구조</span><span class="sxs-lookup"><span data-stu-id="803b8-215">All partition-aligned structures.</span></span>|  
|<span data-ttu-id="803b8-216">CL_IDX</span><span class="sxs-lookup"><span data-stu-id="803b8-216">CL_IDX</span></span>|<span data-ttu-id="803b8-217">테이블에 있는 모든 클러스터형 인덱스</span><span class="sxs-lookup"><span data-stu-id="803b8-217">All clustered indexes on tables</span></span>|  
|<span data-ttu-id="803b8-218">IDX</span><span class="sxs-lookup"><span data-stu-id="803b8-218">IDX</span></span>|<span data-ttu-id="803b8-219">테이블에 있는 모든 클러스터형 및 비클러스터형 인덱스</span><span class="sxs-lookup"><span data-stu-id="803b8-219">All clustered and nonclustered indexes on tables</span></span>|  
  
 <span data-ttu-id="803b8-220">**-fp** _partitioning_strategy_</span><span class="sxs-lookup"><span data-stu-id="803b8-220">**-fp** _partitioning_strategy_</span></span>  
 <span data-ttu-id="803b8-221">**dta** 가 제안하는 새 실제 디자인 구조(인덱스 및 인덱싱된 뷰)를 분할할 것인지 여부와 분할 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-221">Specifies whether new physical design structures (indexes and indexed views) that **dta** proposes should be partitioned, and how they should be partitioned.</span></span> <span data-ttu-id="803b8-222">다음 표에서는 이 인수에 지정할 수 있는 값을 나열하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-222">The following table lists and describes the values that can be specified for this argument:</span></span>  
  
|<span data-ttu-id="803b8-223">값</span><span class="sxs-lookup"><span data-stu-id="803b8-223">Value</span></span>|<span data-ttu-id="803b8-224">Description</span><span class="sxs-lookup"><span data-stu-id="803b8-224">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="803b8-225">없음</span><span class="sxs-lookup"><span data-stu-id="803b8-225">NONE</span></span>|<span data-ttu-id="803b8-226">분할 안 함</span><span class="sxs-lookup"><span data-stu-id="803b8-226">No partitioning</span></span>|  
|<span data-ttu-id="803b8-227">FULL</span><span class="sxs-lookup"><span data-stu-id="803b8-227">FULL</span></span>|<span data-ttu-id="803b8-228">전체 분할(성능 향상 중심)</span><span class="sxs-lookup"><span data-stu-id="803b8-228">Full partitioning (choose to enhance performance)</span></span>|  
|<span data-ttu-id="803b8-229">ALIGNED</span><span class="sxs-lookup"><span data-stu-id="803b8-229">ALIGNED</span></span>|<span data-ttu-id="803b8-230">정렬된 분할만(관리 효율성 향상 중심)</span><span class="sxs-lookup"><span data-stu-id="803b8-230">Aligned partitioning only (choose to enhance manageability)</span></span>|  
  
 <span data-ttu-id="803b8-231">ALIGNED는 **dta** 로 생성된 권장 구성에서 제안된 모든 인덱스가 이 인덱스를 정의한 기본 테이블과 정확히 같은 방식으로 분할됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-231">ALIGNED means that in the recommendation generated by **dta** every proposed index is partitioned in exactly the same way as the underlying table for which the index is defined.</span></span> <span data-ttu-id="803b8-232">인덱싱된 뷰의 비클러스터형 인덱스는 인덱싱된 뷰에 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-232">Nonclustered indexes on an indexed view are aligned with the indexed view.</span></span> <span data-ttu-id="803b8-233">이 인수에는 값을 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-233">Only one value can be specified for this argument.</span></span> <span data-ttu-id="803b8-234">기본값은 **-fp** `NONE` 입니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-234">The default is **-fp**`NONE`.</span></span>  
  
 <span data-ttu-id="803b8-235">**-fx** _drop_only_mode_</span><span class="sxs-lookup"><span data-stu-id="803b8-235">**-fx** _drop_only_mode_</span></span>  
 <span data-ttu-id="803b8-236">**dta** 에서 기존의 실제 디자인 구조의 삭제만 고려할 것인지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-236">Specifies that **dta** only considers dropping existing physical design structures.</span></span> <span data-ttu-id="803b8-237">새 물리적 디자인 구조는 고려되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-237">No new physical design structures are considered.</span></span> <span data-ttu-id="803b8-238">이 옵션을 지정하면 **dta** 는 기존 물리적 디자인 구조의 유용성을 평가하고 거의 사용하지 않는 구조를 삭제할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-238">When this option is specified, **dta** evaluates the usefulness of existing physical design structures and recommends dropping seldom used structures.</span></span> <span data-ttu-id="803b8-239">이 인수에는 값이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-239">This argument takes no values.</span></span> <span data-ttu-id="803b8-240">이 인수는 **-fa**, **-fp**또는 **-fk ALL** 인수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-240">It cannot be used with the **-fa**, **-fp**, or **-fk ALL** arguments</span></span>  
  
 <span data-ttu-id="803b8-241">**-ID** _session_ID_</span><span class="sxs-lookup"><span data-stu-id="803b8-241">**-ID** _session_ID_</span></span>  
 <span data-ttu-id="803b8-242">튜닝 세션에 대한 숫자 식별자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-242">Specifies a numerical identifier for the tuning session.</span></span> <span data-ttu-id="803b8-243">이 옵션을 지정하지 않으면 **dta** 는 ID 번호를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-243">If not specified, then **dta** generates an ID number.</span></span> <span data-ttu-id="803b8-244">이 식별자를 사용하여 기존 튜닝 세션에 대한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-244">You can use this identifier to view information for existing tuning sessions.</span></span> <span data-ttu-id="803b8-245">**-ID**값을 지정하지 않을 경우 **-s**를 사용하여 세션 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-245">If you do not specify a value for **-ID**, then a session name must be specified with **-s**.</span></span>  
  
 <span data-ttu-id="803b8-246">**-ip**</span><span class="sxs-lookup"><span data-stu-id="803b8-246">**-ip**</span></span>  
 <span data-ttu-id="803b8-247">계획 캐시를 작업으로 사용할 수 있도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-247">Specifies that the plan cache be used as the workload.</span></span> <span data-ttu-id="803b8-248">명시적으로 선택한 데이터베이스에 대한 상위 1,000개의 계획 캐시 이벤트가 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-248">The top 1,000 plan cache events for explicitly selected databases are analyzed.</span></span> <span data-ttu-id="803b8-249">**–n** 옵션을 사용하여 이 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-249">This value can be changed using the **-n** option.</span></span>  
  
 <span data-ttu-id="803b8-250">**-ipf**</span><span class="sxs-lookup"><span data-stu-id="803b8-250">**-ipf**</span></span>  
 <span data-ttu-id="803b8-251">계획 캐시를 작업으로 사용할 수 있도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-251">Specifies that the plan cache be used as the workload.</span></span> <span data-ttu-id="803b8-252">모든 데이터베이스에 대한 상위 1,000개의 계획 캐시 이벤트가 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-252">The top 1,000 plan cache events for all databases are analyzed.</span></span> <span data-ttu-id="803b8-253">**–n** 옵션을 사용하여 이 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-253">This value can be changed using the **-n** option.</span></span>  
  
 <span data-ttu-id="803b8-254">**-if** _workload_file_</span><span class="sxs-lookup"><span data-stu-id="803b8-254">**-if** _workload_file_</span></span>  
 <span data-ttu-id="803b8-255">튜닝을 위한 입력으로 사용할 작업 파일의 경로와 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-255">Specifies the path and name of the workload file to use as input for tuning.</span></span> <span data-ttu-id="803b8-256">파일은 .trc(SQL Server Profiler 추적 파일), .sql(SQL 파일) 또는 .log([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 추적 파일) 형식 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-256">The file must be in one of these formats: .trc (SQL Server Profiler trace file), .sql (SQL file), or .log ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trace file).</span></span> <span data-ttu-id="803b8-257">작업 파일 또는 작업 테이블을 하나 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-257">Either one workload file or one workload table must be specified.</span></span>  
  
 <span data-ttu-id="803b8-258">**-it** _workload_trace_table_name_</span><span class="sxs-lookup"><span data-stu-id="803b8-258">**-it** _workload_trace_table_name_</span></span>  
 <span data-ttu-id="803b8-259">튜닝을 위한 작업 추적을 포함하는 테이블의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-259">Specifies the name of a table containing the workload trace for tuning.</span></span> <span data-ttu-id="803b8-260">이름은 [*database_name*] **.** [*owner_name*] **.** _table_name_형식으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-260">The name is specified in the format: [*database_name*]**.**[*owner_name*]**.**_table_name_.</span></span>  
  
 <span data-ttu-id="803b8-261">다음 표에서는 각 매개 변수의 기본값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-261">The following table shows the default values for each:</span></span>  
  
|<span data-ttu-id="803b8-262">매개 변수</span><span class="sxs-lookup"><span data-stu-id="803b8-262">Parameter</span></span>|<span data-ttu-id="803b8-263">기본값</span><span class="sxs-lookup"><span data-stu-id="803b8-263">Default value</span></span>|  
|---------------|-------------------|  
|<span data-ttu-id="803b8-264">*database_name*</span><span class="sxs-lookup"><span data-stu-id="803b8-264">*database_name*</span></span>|<span data-ttu-id="803b8-265">*–D* 옵션으로 지정된 **database_name**</span><span class="sxs-lookup"><span data-stu-id="803b8-265">*database_name* specified with **-D** option.</span></span>|  
|<span data-ttu-id="803b8-266">*owner_name*</span><span class="sxs-lookup"><span data-stu-id="803b8-266">*owner_name*</span></span>|<span data-ttu-id="803b8-267">**dbo**</span><span class="sxs-lookup"><span data-stu-id="803b8-267">**dbo**.</span></span>|  
|<span data-ttu-id="803b8-268">*table_name*</span><span class="sxs-lookup"><span data-stu-id="803b8-268">*table_name*</span></span>|<span data-ttu-id="803b8-269">없음</span><span class="sxs-lookup"><span data-stu-id="803b8-269">None.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="803b8-270">*owner_name* 은 **dbo**여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-270">*owner_name* must be **dbo**.</span></span> <span data-ttu-id="803b8-271">다른 값을 지정하면 **dta** 가 실행되지 않고 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-271">If any other value is specified, execution of **dta** fails and an error is returned.</span></span> <span data-ttu-id="803b8-272">작업 파일 또는 작업 테이블 하나를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-272">Also note that either one workload table or one workload file must be specified.</span></span>  
  
 <span data-ttu-id="803b8-273">**-ix** _input_XML_file_name_</span><span class="sxs-lookup"><span data-stu-id="803b8-273">**-ix** _input_XML_file_name_</span></span>  
 <span data-ttu-id="803b8-274">**dta** 입력 정보가 포함된 XML 파일의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-274">Specifies the name of the XML file containing **dta** input information.</span></span> <span data-ttu-id="803b8-275">이 파일은 DTASchema.xsd를 준수하는 유효한 XML 문서여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-275">This must be a valid XML document conforming to DTASchema.xsd.</span></span> <span data-ttu-id="803b8-276">명령 프롬프트에서 튜닝 옵션에 대해 지정한 인수와 충돌하면 이 XML 파일의 해당 값보다 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-276">Conflicting arguments specified from the command prompt for tuning options override the corresponding value in this XML file.</span></span> <span data-ttu-id="803b8-277">단, 사용자 지정 구성을 XML 입력 파일에 평가 모드로 입력할 경우는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-277">The only exception is if a user-specified configuration is entered in the evaluate mode in the XML input file.</span></span> <span data-ttu-id="803b8-278">예를 들어 XML 입력 파일의 **Configuration** 요소에 구성을 입력하고 튜닝 옵션 중 하나로 **EvaluateConfiguration** 요소를 지정한 경우 XML 입력 파일에서 지정한 튜닝 옵션은 명령 프롬프트에서 입력한 튜닝 옵션보다 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-278">For example, if a configuration is entered in the **Configuration** element of the XML input file and the **EvaluateConfiguration** element is also specified as one of the tuning options, the tuning options specified in the XML input file will override any tuning options entered from the command prompt.</span></span>  
  
 <span data-ttu-id="803b8-279">**-m** _minimum_improvement_</span><span class="sxs-lookup"><span data-stu-id="803b8-279">**-m** _minimum_improvement_</span></span>  
 <span data-ttu-id="803b8-280">권장 구성이 만족시켜야 할 최소 향상률을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-280">Specifies the minimum percentage of improvement that the recommended configuration must satisfy.</span></span>  
  
 <span data-ttu-id="803b8-281">**-N** _online_option_</span><span class="sxs-lookup"><span data-stu-id="803b8-281">**-N** _online_option_</span></span>  
 <span data-ttu-id="803b8-282">물리적 디자인 구조를 온라인으로 만들 것인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-282">Specifies whether physical design structures are created online.</span></span> <span data-ttu-id="803b8-283">다음 표에서는 이 인수에 지정할 수 있는 값을 나열하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-283">The following table lists and describes the values you can specify for this argument:</span></span>  
  
|<span data-ttu-id="803b8-284">값</span><span class="sxs-lookup"><span data-stu-id="803b8-284">Value</span></span>|<span data-ttu-id="803b8-285">Description</span><span class="sxs-lookup"><span data-stu-id="803b8-285">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="803b8-286">OFF</span><span class="sxs-lookup"><span data-stu-id="803b8-286">OFF</span></span>|<span data-ttu-id="803b8-287">권장되는 물리적 디자인 구조를 온라인으로 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-287">No recommended physical design structures can be created online.</span></span>|  
|<span data-ttu-id="803b8-288">켜기</span><span class="sxs-lookup"><span data-stu-id="803b8-288">ON</span></span>|<span data-ttu-id="803b8-289">권장되는 모든 물리적 디자인 구조를 온라인으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-289">All recommended physical design structures can be created online.</span></span>|  
|<span data-ttu-id="803b8-290">MIXED</span><span class="sxs-lookup"><span data-stu-id="803b8-290">MIXED</span></span>|<span data-ttu-id="803b8-291">데이터베이스 엔진 튜닝 관리자는 가능한 경우 온라인으로 만들 수 있는 물리적 디자인 구조를 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-291">Database Engine Tuning Advisor attempts to recommend physical design structures that can be created online when possible.</span></span>|  
  
 <span data-ttu-id="803b8-292">인덱스를 온라인으로 만드는 경우 개체 정의에 ONLINE = ON이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-292">If indexes are created online, ONLINE = ON is appended to its object definition.</span></span>  
  
 <span data-ttu-id="803b8-293">**-n** _number_of_events_</span><span class="sxs-lookup"><span data-stu-id="803b8-293">**-n** _number_of_events_</span></span>  
 <span data-ttu-id="803b8-294">**dta** 가 튜닝해야 할 작업의 이벤트 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-294">Specifies the number of events in the workload that **dta** should tune.</span></span> <span data-ttu-id="803b8-295">이 인수를 지정한 경우 작업이 기간 정보가 포함된 추적 파일이면 **dta** 는 기간의 내림차순으로 이벤트를 튜닝합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-295">If this argument is specified and the workload is a trace file that contains duration information, then **dta** tunes events in decreasing order of duration.</span></span> <span data-ttu-id="803b8-296">이 인수는 물리적 디자인 구조의 두 구성을 비교할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-296">This argument is useful to compare two configurations of physical design structures.</span></span> <span data-ttu-id="803b8-297">두 구성을 비교하려면 다음과 같이 두 구성에 대해 튜닝할 이벤트 수를 같은 값으로 지정하고 무제한 튜닝 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-297">To compare two configurations, specify the same number of events to be tuned for both configurations and then specify an unlimited tuning time for both also as follows:</span></span>  
  
```  
dta -n number_of_events -A 0  
```  
  
 <span data-ttu-id="803b8-298">이러한 경우 반드시 무제한 튜닝 시간(`-A 0`)을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-298">In this case, it is important to specify an unlimited tuning time (`-A 0`).</span></span> <span data-ttu-id="803b8-299">그렇지 않으면 기본적으로 데이터베이스 엔진 튜닝 관리자에서 튜닝 시간으로 8시간을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-299">Otherwise, Database Engine Tuning Advisor assumes an 8 hour tuning time by default.</span></span>  
  
 <span data-ttu-id="803b8-300">**-of** _output_script_file_name_</span><span class="sxs-lookup"><span data-stu-id="803b8-300">**-of** _output_script_file_name_</span></span>  
 <span data-ttu-id="803b8-301">**dta** 가 권장 구성을 지정된 파일 이름 및 대상에 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트로 쓰도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-301">Specifies that **dta** writes the recommendation as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script to the file name and destination specified.</span></span>  
  
 <span data-ttu-id="803b8-302">이 옵션과 함께 **-F** 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-302">You can use **-F** with this option.</span></span> <span data-ttu-id="803b8-303">파일 이름이 고유한지 확인합니다. 특히 **-or** 및 **-ox**를 함께 사용하는 경우 고유한 파일 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-303">Make sure that the file name is unique, especially if you are also using **-or** and **-ox**.</span></span>  
  
 <span data-ttu-id="803b8-304">**-or** _output_xml_report_file_name_</span><span class="sxs-lookup"><span data-stu-id="803b8-304">**-or** _output_xml_report_file_name_</span></span>  
 <span data-ttu-id="803b8-305">**dta** 가 권장 구성을 XML 형식의 출력 보고서로 쓰도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-305">Specifies that **dta** writes the recommendation to an output report in XML.</span></span> <span data-ttu-id="803b8-306">파일 이름을 제공한 경우 권장 구성이 해당 대상에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-306">If a file name is supplied, then the recommendations are written to that destination.</span></span> <span data-ttu-id="803b8-307">그렇지 않으면 **dta** 는 세션 이름을 사용하여 파일 이름을 생성하고 현재 디렉터리에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-307">Otherwise, **dta** uses the session name to generate the file name and writes it to the current directory.</span></span>  
  
 <span data-ttu-id="803b8-308">이 옵션과 함께 **-F** 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-308">You can use **-F** with this option.</span></span> <span data-ttu-id="803b8-309">파일 이름이 고유한지 확인합니다. 특히 **-of** 및 **-ox**를 함께 사용하는 경우 고유한 파일 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-309">Make sure that the file name is unique, especially if you are also using **-of** and **-ox**.</span></span>  
  
 <span data-ttu-id="803b8-310">**-ox** _output_XML_file_name_</span><span class="sxs-lookup"><span data-stu-id="803b8-310">**-ox** _output_XML_file_name_</span></span>  
 <span data-ttu-id="803b8-311">**dta** 가 권장 구성을 제공된 파일 이름 및 대상에 XML 파일로 쓰도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-311">Specifies that **dta** writes the recommendation as an XML file to the file name and destination supplied.</span></span> <span data-ttu-id="803b8-312">데이터베이스 엔진 튜닝 관리자에서 대상 디렉터리에 쓸 수 있는 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-312">Ensure that Database Engine Tuning Advisor has permissions to write to the destination directory.</span></span>  
  
 <span data-ttu-id="803b8-313">이 옵션과 함께 **-F** 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-313">You can use **-F** with this option.</span></span> <span data-ttu-id="803b8-314">파일 이름이 고유한지 확인합니다. 특히 **-of** 및 **-or**을 함께 사용하는 경우 고유한 파일 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-314">Make sure that the file name is unique, especially if you are also using **-of** and **-or**.</span></span>  
  
 <span data-ttu-id="803b8-315">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="803b8-315">**-P** _password_</span></span>  
 <span data-ttu-id="803b8-316">로그인 ID의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-316">Specifies the password for the login ID.</span></span> <span data-ttu-id="803b8-317">이 옵션을 사용하지 않으면 **dta** 가 암호를 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-317">If this option is not used, **dta** prompts for a password.</span></span>  
  
 <span data-ttu-id="803b8-318">**-q**</span><span class="sxs-lookup"><span data-stu-id="803b8-318">**-q**</span></span>  
 <span data-ttu-id="803b8-319">자동 모드를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-319">Sets quiet mode.</span></span> <span data-ttu-id="803b8-320">진행률 및 머리글 정보를 포함하여 어떤 정보도 콘솔에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-320">No information is written to the console, including progress and header information.</span></span>  
  
 <span data-ttu-id="803b8-321">**-rl** _analysis_report_list_</span><span class="sxs-lookup"><span data-stu-id="803b8-321">**-rl** _analysis_report_list_</span></span>  
 <span data-ttu-id="803b8-322">생성할 분석 보고서의 목록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-322">Specifies the list of analysis reports to generate.</span></span> <span data-ttu-id="803b8-323">다음 표에서는 이 인수에 지정할 수 있는 값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-323">The following table lists the values that can be specified for this argument:</span></span>  
  
|<span data-ttu-id="803b8-324">값</span><span class="sxs-lookup"><span data-stu-id="803b8-324">Value</span></span>|<span data-ttu-id="803b8-325">보고서</span><span class="sxs-lookup"><span data-stu-id="803b8-325">Report</span></span>|  
|-----------|------------|  
|<span data-ttu-id="803b8-326">ALL</span><span class="sxs-lookup"><span data-stu-id="803b8-326">ALL</span></span>|<span data-ttu-id="803b8-327">모든 분석 보고서</span><span class="sxs-lookup"><span data-stu-id="803b8-327">All analysis reports</span></span>|  
|<span data-ttu-id="803b8-328">STMT_COST</span><span class="sxs-lookup"><span data-stu-id="803b8-328">STMT_COST</span></span>|<span data-ttu-id="803b8-329">문 비용 보고서</span><span class="sxs-lookup"><span data-stu-id="803b8-329">Statement cost report</span></span>|  
|<span data-ttu-id="803b8-330">EVT_FREQ</span><span class="sxs-lookup"><span data-stu-id="803b8-330">EVT_FREQ</span></span>|<span data-ttu-id="803b8-331">이벤트 빈도 보고서</span><span class="sxs-lookup"><span data-stu-id="803b8-331">Event frequency report</span></span>|  
|<span data-ttu-id="803b8-332">STMT_DET</span><span class="sxs-lookup"><span data-stu-id="803b8-332">STMT_DET</span></span>|<span data-ttu-id="803b8-333">문 세부 정보 보고서</span><span class="sxs-lookup"><span data-stu-id="803b8-333">Statement detail report</span></span>|  
|<span data-ttu-id="803b8-334">CUR_STMT_IDX</span><span class="sxs-lookup"><span data-stu-id="803b8-334">CUR_STMT_IDX</span></span>|<span data-ttu-id="803b8-335">문-인덱스 관계 보고서(현재 구성)</span><span class="sxs-lookup"><span data-stu-id="803b8-335">Statement-index relations report (current configuration)</span></span>|  
|<span data-ttu-id="803b8-336">REC_STMT_IDX</span><span class="sxs-lookup"><span data-stu-id="803b8-336">REC_STMT_IDX</span></span>|<span data-ttu-id="803b8-337">문-인덱스 관계 보고서(권장 구성)</span><span class="sxs-lookup"><span data-stu-id="803b8-337">Statement-index relations report (recommended configuration)</span></span>|  
|<span data-ttu-id="803b8-338">STMT_COSTRANGE</span><span class="sxs-lookup"><span data-stu-id="803b8-338">STMT_COSTRANGE</span></span>|<span data-ttu-id="803b8-339">문 비용 범위 보고서</span><span class="sxs-lookup"><span data-stu-id="803b8-339">Statement cost range report</span></span>|  
|<span data-ttu-id="803b8-340">CUR_IDX_USAGE</span><span class="sxs-lookup"><span data-stu-id="803b8-340">CUR_IDX_USAGE</span></span>|<span data-ttu-id="803b8-341">인덱스 사용 보고서(현재 구성)</span><span class="sxs-lookup"><span data-stu-id="803b8-341">Index usage report (current configuration)</span></span>|  
|<span data-ttu-id="803b8-342">REC_IDX_USAGE</span><span class="sxs-lookup"><span data-stu-id="803b8-342">REC_IDX_USAGE</span></span>|<span data-ttu-id="803b8-343">인덱스 사용 보고서(권장 구성)</span><span class="sxs-lookup"><span data-stu-id="803b8-343">Index usage report (recommended configuration)</span></span>|  
|<span data-ttu-id="803b8-344">CUR_IDX_DET</span><span class="sxs-lookup"><span data-stu-id="803b8-344">CUR_IDX_DET</span></span>|<span data-ttu-id="803b8-345">인덱스 세부 정보 보고서(현재 구성)</span><span class="sxs-lookup"><span data-stu-id="803b8-345">Index detail report (current configuration)</span></span>|  
|<span data-ttu-id="803b8-346">REC_IDX_DET</span><span class="sxs-lookup"><span data-stu-id="803b8-346">REC_IDX_DET</span></span>|<span data-ttu-id="803b8-347">인덱스 세부 정보 보고서(권장 구성)</span><span class="sxs-lookup"><span data-stu-id="803b8-347">Index detail report (recommended configuration)</span></span>|  
|<span data-ttu-id="803b8-348">VIW_TAB</span><span class="sxs-lookup"><span data-stu-id="803b8-348">VIW_TAB</span></span>|<span data-ttu-id="803b8-349">뷰-테이블 관계 보고서</span><span class="sxs-lookup"><span data-stu-id="803b8-349">View-table relations report</span></span>|  
|<span data-ttu-id="803b8-350">WKLD_ANL</span><span class="sxs-lookup"><span data-stu-id="803b8-350">WKLD_ANL</span></span>|<span data-ttu-id="803b8-351">작업 분석 보고서</span><span class="sxs-lookup"><span data-stu-id="803b8-351">Workload analysis report</span></span>|  
|<span data-ttu-id="803b8-352">DB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="803b8-352">DB_ACCESS</span></span>|<span data-ttu-id="803b8-353">데이터베이스 액세스 보고서</span><span class="sxs-lookup"><span data-stu-id="803b8-353">Database access report</span></span>|  
|<span data-ttu-id="803b8-354">TAB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="803b8-354">TAB_ACCESS</span></span>|<span data-ttu-id="803b8-355">테이블 액세스 보고서</span><span class="sxs-lookup"><span data-stu-id="803b8-355">Table access report</span></span>|  
|<span data-ttu-id="803b8-356">COL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="803b8-356">COL_ACCESS</span></span>|<span data-ttu-id="803b8-357">열 액세스 보고서</span><span class="sxs-lookup"><span data-stu-id="803b8-357">Column access report</span></span>|  
  
 <span data-ttu-id="803b8-358">보고서가 여러 개인 경우 다음과 같이 쉼표로 값을 구분하여 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-358">Specify multiple reports by separating the values with commas, for example:</span></span>  
  
```  
... -rl EVT_FREQ, VIW_TAB, WKLD_ANL ...  
```  
  
 <span data-ttu-id="803b8-359">**-S** _server_name_[ *\instance*]</span><span class="sxs-lookup"><span data-stu-id="803b8-359">**-S** _server_name_[ *\instance*]</span></span>  
 <span data-ttu-id="803b8-360">연결할 컴퓨터 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-360">Specifies the name of the computer and instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to connect to.</span></span> <span data-ttu-id="803b8-361">*server_name* 을 지정하지 않으면 **dta** 가 로컬 컴퓨터에 있는 기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-361">If no *server_name* is specified, **dta** connects to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="803b8-362">명명된 인스턴스에 연결할 때 또는 네트워크의 원격 컴퓨터에서 **dta** 를 실행할 때 이 옵션을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-362">This option is required when connecting to a named instance or when executing **dta** from a remote computer on the network.</span></span>  
  
 <span data-ttu-id="803b8-363">**-s** _session_name_</span><span class="sxs-lookup"><span data-stu-id="803b8-363">**-s** _session_name_</span></span>  
 <span data-ttu-id="803b8-364">튜닝 세션 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-364">Specifies the name of the tuning session.</span></span> <span data-ttu-id="803b8-365">**-ID** 를 지정하지 않는 경우 이 인수를 반드시 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-365">This is required if **-ID** is not specified.</span></span>  
  
 <span data-ttu-id="803b8-366">**-Tf** _table_list_file_</span><span class="sxs-lookup"><span data-stu-id="803b8-366">**-Tf** _table_list_file_</span></span>  
 <span data-ttu-id="803b8-367">튜닝할 테이블 목록이 들어 있는 파일의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-367">Specifies the name of a file containing a list of tables to be tuned.</span></span> <span data-ttu-id="803b8-368">파일 내에 표시된 각 테이블은 새 줄로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-368">Each table listed within the file should begin on a new line.</span></span> <span data-ttu-id="803b8-369">테이블 이름은 **AdventureWorks2012.HumanResources.Department**와 같이 세 부분으로 이루어진 정규화된 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-369">Table names should be qualified with three-part naming, for example, **AdventureWorks2012.HumanResources.Department**.</span></span> <span data-ttu-id="803b8-370">또한 테이블 배율 기능을 호출하려면 기존 테이블 이름 뒤에 테이블의 예상 행 수를 나타내는 숫자를 붙일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-370">Optionally, to invoke the table-scaling feature, the name of an existing table can be followed by a number indicating the projected number of rows in the table.</span></span> <span data-ttu-id="803b8-371">데이터베이스 엔진 튜닝 관리자에서는 이 테이블을 참조하는 작업에서 문을 튜닝하거나 평가하는 동안 예상 행 수를 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-371">Database Engine Tuning Advisor takes into consideration the projected number of rows while tuning or evaluating statements in the workload that reference these tables.</span></span> <span data-ttu-id="803b8-372">*number_of_rows* 개수와 *table_name*사이에 하나 이상의 공백이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-372">Note that there can be one or more spaces between the *number_of_rows* count and the *table_name*.</span></span>  
  
 <span data-ttu-id="803b8-373">다음은 *table_list_file*의 파일 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-373">This is the file format for *table_list_file*:</span></span>  
  
 <span data-ttu-id="803b8-374">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span><span class="sxs-lookup"><span data-stu-id="803b8-374">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span></span>  
  
 <span data-ttu-id="803b8-375">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span><span class="sxs-lookup"><span data-stu-id="803b8-375">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span></span>  
  
 <span data-ttu-id="803b8-376">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span><span class="sxs-lookup"><span data-stu-id="803b8-376">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span></span>  
  
 <span data-ttu-id="803b8-377">이 인수는 명령 프롬프트에서 테이블 목록( **-Tl**)을 입력하는 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-377">This argument is an alternative to entering a table list at the command prompt (**-Tl**).</span></span> <span data-ttu-id="803b8-378">**-Tl**를 사용하는 경우 테이블 목록 파일( **-Tf**)을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="803b8-378">Do not use a table list file (**-Tf**) if you are using **-Tl**.</span></span> <span data-ttu-id="803b8-379">두 인수를 모두 사용하면 **dta** 가 실패하고 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-379">If both arguments are used, **dta** fails and returns an error.</span></span>  
  
 <span data-ttu-id="803b8-380">**-Tf** 및 **-Tl** 인수를 둘 다 생략하면 지정한 데이터베이스의 모든 사용자 테이블이 튜닝 대상으로 고려됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-380">If the **-Tf** and **-Tl** arguments are omitted, all user tables in the specified databases are considered for tuning.</span></span>  
  
 <span data-ttu-id="803b8-381">**-Tl** _table_list_</span><span class="sxs-lookup"><span data-stu-id="803b8-381">**-Tl** _table_list_</span></span>  
 <span data-ttu-id="803b8-382">명령 프롬프트에서 튜닝할 테이블 목록을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-382">Specifies at the command prompt a list of tables to be tuned.</span></span> <span data-ttu-id="803b8-383">테이블 이름은 쉼표를 입력하여 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-383">Place commas between table names to separate them.</span></span> <span data-ttu-id="803b8-384">**-D** 인수로 데이터베이스를 하나만 지정하는 경우 데이터베이스 이름으로 테이블 이름을 정규화할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-384">If only one database is specified with the **-D** argument, then table names do not need to be qualified with a database name.</span></span> <span data-ttu-id="803b8-385">그렇지 않고 여러 데이터베이스를 지정하는 경우에는 각 테이블에 *database_name.schema_name.table_name* 형식으로 정규화된 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-385">Otherwise, the fully qualified name in the format: *database_name.schema_name.table_name* is required for each table.</span></span>  
  
 <span data-ttu-id="803b8-386">이 인수는 테이블 목록 파일( **-Tf**) 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-386">This argument is an alternative to using a table list file (**-Tf**).</span></span> <span data-ttu-id="803b8-387">**-Tl** 및 **-Tf** 를 모두 사용하면 **dta** 가 실패하고 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-387">If both **-Tl** and **-Tf** are used, **dta** fails and returns an error.</span></span>  
  
 <span data-ttu-id="803b8-388">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="803b8-388">**-U** _login_id_</span></span>  
 <span data-ttu-id="803b8-389">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]연결에 사용하는 로그인 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-389">Specifies the login ID used to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="803b8-390">**-u**</span><span class="sxs-lookup"><span data-stu-id="803b8-390">**-u**</span></span>  
 <span data-ttu-id="803b8-391">데이터베이스 엔진 튜닝 관리자 GUI를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-391">Launches the Database Engine Tuning Advisor GUI.</span></span> <span data-ttu-id="803b8-392">모든 매개 변수는 사용자 인터페이스의 초기 설정으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-392">All parameters are treated as the initial settings for the user interface.</span></span>  
  
 <span data-ttu-id="803b8-393">**-x**</span><span class="sxs-lookup"><span data-stu-id="803b8-393">**-x**</span></span>  
 <span data-ttu-id="803b8-394">튜닝 세션을 시작하고 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-394">Starts tuning session and exits.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="803b8-395">설명</span><span class="sxs-lookup"><span data-stu-id="803b8-395">Remarks</span></span>  
 <span data-ttu-id="803b8-396">Ctrl+C를 한 번 누르면 튜닝 세션이 중지되고 이 지점까지 **dta** 가 완료한 분석을 기반으로 권장 구성이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-396">Press CTRL+C once to stop the tuning session and generate recommendations based on the analysis **dta** has completed up to this point.</span></span> <span data-ttu-id="803b8-397">권장 구성을 생성할지 여부를 결정하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-397">You will be prompted to decide whether you want to generate recommendations or not.</span></span> <span data-ttu-id="803b8-398">Ctrl+C를 다시 누르면 권장 구성을 생성하지 않고 튜닝 세션이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-398">Press CTRL+C again to stop the tuning session without generating recommendations.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="803b8-399">예</span><span class="sxs-lookup"><span data-stu-id="803b8-399">Examples</span></span>  
 <span data-ttu-id="803b8-400">**A. 권장 구성에 인덱스 및 인덱싱된 뷰가 포함된 작업 튜닝**</span><span class="sxs-lookup"><span data-stu-id="803b8-400">**A. Tune a workload that includes indexes and indexed views in its recommendation**</span></span>  
  
 <span data-ttu-id="803b8-401">이 예에서는 보안 연결(`-E`)을 통해 MyServer에 있는 **tpcd1G** 데이터베이스에 연결하여 작업을 분석하고 권장 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-401">This example uses a secure connection (`-E`) to connect to the **tpcd1G** database on MyServer to analyze a workload and create recommendations.</span></span> <span data-ttu-id="803b8-402">그리고 script.sql이라는 스크립트 파일에 출력 파일을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-402">It writes the output to a script file named script.sql.</span></span> <span data-ttu-id="803b8-403">script.sql이 이미 있을 경우 **인수를 지정했으므로** dta `-F` 는 이 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-403">If script.sql already exists, then **dta** will overwrite the file because the `-F` argument has been specified.</span></span> <span data-ttu-id="803b8-404">작업 분석이 완료될 때까지 제한 시간 없이(`-A 0`) 튜닝 세션이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-404">The tuning session runs for an unlimited length of time to ensure a complete analysis of the workload (`-A 0`).</span></span> <span data-ttu-id="803b8-405">권장 구성에서는 최소 향상률 값으로 5%(`-m 5`)를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-405">The recommendation must provide a minimum improvement of 5% (`-m 5`).</span></span> <span data-ttu-id="803b8-406">**dta** 는 최종 권장 구성(`-fa IDX_IV`)에 인덱스 및 인덱싱된 뷰를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-406">**dta** should include indexes and indexed views in its final recommendation (`-fa IDX_IV`).</span></span>  
  
```  
dta -S MyServer -E -D tpcd1G -if tpcd_22.sql -F -of script.sql -A 0 -m 5 -fa IDX_IV  
```  
  
 <span data-ttu-id="803b8-407">**B. 디스크 사용 제한**</span><span class="sxs-lookup"><span data-stu-id="803b8-407">**B. Limit disk use**</span></span>  
  
 <span data-ttu-id="803b8-408">이 예에서는 원시 데이터 및 추가 인덱스를 포함하여 총 데이터베이스 크기를 3GB(`-B 3000`)로 제한하고 출력을 d:\result_dir\script1.sql로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-408">This example limits the total database size, which includes the raw data and the additional indexes, to 3 gigabytes (GB) (`-B 3000`) and directs the output to d:\result_dir\script1.sql.</span></span> <span data-ttu-id="803b8-409">1시간(`-A 60`) 동안만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-409">It runs for no more than 1 hour (`-A 60`).</span></span>  
  
```  
dta -D tpcd1G -if tpcd_22.sql -B 3000 -of "d:\result_dir\script1.sql" -A 60  
```  
  
 <span data-ttu-id="803b8-410">**C. 튜닝 쿼리 수 제한**</span><span class="sxs-lookup"><span data-stu-id="803b8-410">**C. Limit the number of tuned queries**</span></span>  
  
 <span data-ttu-id="803b8-411">이 예에서는 orders_wkld.sql 파일에서 읽혀지는 최대 쿼리 수를 10(`-n 10`)개로 제한하고 15분(`-A 15`) 동안 실행합니다. 최대 쿼리 10개에 도달하거나 15분이 되면 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-411">This example limits the number of queries read from the file orders_wkld.sql to a maximum of 10 (`-n 10`) and runs for 15 minutes (`-A 15`), whichever comes first.</span></span> <span data-ttu-id="803b8-412">10개 쿼리를 모두 튜닝하려면 `-A 0`을 사용하여 튜닝 시간을 무제한으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-412">To make sure that all 10 queries are tuned, specify an unlimited tuning time with `-A 0`.</span></span> <span data-ttu-id="803b8-413">시간이 중요할 경우 다음 예와 같이 `-A` 인수로 튜닝할 수 있는 시간(분)을 지정하여 적절한 제한 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-413">If time is important, specify an appropriate time limit by specifying the number of minutes that are available for tuning with the `-A` argument as shown in this example.</span></span>  
  
```  
dta -D orders -if orders_wkld.sql -of script.sql -A 15 -n 10  
```  
  
 <span data-ttu-id="803b8-414">**D. 파일에 나열된 특정 테이블 튜닝**</span><span class="sxs-lookup"><span data-stu-id="803b8-414">**D. Tune specific tables listed in a file**</span></span>  
  
 <span data-ttu-id="803b8-415">이 예에서는 *table_list_file* ( **-Tf** 인수)을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-415">This example demonstrates the use of *table_list_file* (the **-Tf** argument).</span></span> <span data-ttu-id="803b8-416">table_list.txt 파일 내용은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-416">The contents of the file table_list.txt are as follows:</span></span>  
  
```  
AdventureWorks2012.Sales.Customer  100000  
AdventureWorks2012.Sales.Store  
AdventureWorks2012.Production.Product  2000000  
```  
  
 <span data-ttu-id="803b8-417">table_list.txt의 내용은 다음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-417">The contents of table_list.txt specifies that:</span></span>  
  
-   <span data-ttu-id="803b8-418">데이터베이스에서 **Customer**, **Store**및 **Product** 테이블만 튜닝해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-418">Only the **Customer**, **Store**, and **Product** tables in the database should be tuned.</span></span>  
  
-   <span data-ttu-id="803b8-419">**Customer** 및 **Product** 테이블의 행 수는 각각 100,000개와 2,000,000개로 가정됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-419">The number of rows in the **Customer** and **Product** tables are assumed to be 100,000 and 2,000,000, respectively.</span></span>  
  
-   <span data-ttu-id="803b8-420">**Store** 의 행 수는 테이블에 있는 현재 행 수로 가정됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-420">The number of rows in **Store** are assumed to be the current number of rows in the table.</span></span>  
  
 <span data-ttu-id="803b8-421">*table_list_file*에서 행 개수와 앞 테이블 이름 사이에 하나 이상의 공백이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-421">Note that there can be one or more spaces between the number of rows count and the preceding table name in the *table_list_file*.</span></span>  
  
 <span data-ttu-id="803b8-422">튜닝 시간은 2시간(`-A 120`)이며 출력은 XML 파일(`-ox XMLTune.xml`)에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="803b8-422">The tuning time is 2 hours (`-A 120`) and the output is written to an XML file (`-ox XMLTune.xml`).</span></span>  
  
```  
dta -D pubs -if pubs_wkld.sql -ox XMLTune.xml -A 120 -Tf table_list.txt  
```  
  
## <a name="see-also"></a><span data-ttu-id="803b8-423">참고 항목</span><span class="sxs-lookup"><span data-stu-id="803b8-423">See Also</span></span>  
 <span data-ttu-id="803b8-424">[명령 프롬프트 유틸리티 참조 &#40;데이터베이스 엔진&#41;](../command-prompt-utility-reference-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="803b8-424">[Command Prompt Utility Reference &#40;Database Engine&#41;](../command-prompt-utility-reference-database-engine.md) </span></span>  
 [<span data-ttu-id="803b8-425">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="803b8-425">Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
