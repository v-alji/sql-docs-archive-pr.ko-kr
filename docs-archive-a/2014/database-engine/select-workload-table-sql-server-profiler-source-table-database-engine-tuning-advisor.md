---
title: SQL Server Profiler-원본 테이블-데이터베이스 엔진 튜닝 관리자-작업 테이블 선택 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.replay.tools.sourcetable.f1
helpviewer_keywords:
- Select Workload Table dialog box
- Source Table dialog box
ms.assetid: 51185be7-7092-480a-a52c-cf7786c4a0a0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d10899c01df8e7fbc7ee45d108841a18d3248500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649663"
---
# <a name="sql-server-profiler---source-table-database-engine-tuning-advisor---select-workload-table"></a><span data-ttu-id="18151-102">SQL Server Profiler - Source Table-Database Engine Tuning Advisor - Select Workload Table</span><span class="sxs-lookup"><span data-stu-id="18151-102">SQL Server Profiler - Source Table-Database Engine Tuning Advisor - Select Workload Table</span></span>
  <span data-ttu-id="18151-103">Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 및 [!INCLUDE[ssDE](../includes/ssde-md.md)] 튜닝 관리자는 이 대화 상자를 사용하여 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="18151-103">Microsoft [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] and [!INCLUDE[ssDE](../includes/ssde-md.md)] Tuning Advisor use this dialog box to select tables.</span></span>  
  
 <span data-ttu-id="18151-104">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]에서 추적 테이블의 원본 테이블을 지정하려면 **원본 테이블** 대화 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="18151-104">In [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], use the **Source Table** dialog box to specify a source table for a trace table.</span></span> <span data-ttu-id="18151-105">추적 테이블은 추적 내용이 로드되는 테이블이고 이 테이블의 내용은 추적 재생을 위해 검토되거나 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="18151-105">This is a table from which a trace is loaded, and the contents of which are viewed or used for replaying the trace.</span></span>  
  
 <span data-ttu-id="18151-106">[!INCLUDE[ssDE](../includes/ssde-md.md)] 튜닝 관리자에서는 **작업 테이블 선택** 대화 상자를 사용하여 튜닝 작업으로 사용할 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 추적 정보가 포함된 데이터베이스 테이블을 선택하거나 튜닝 분석 시작 전에 테이블 내용을 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18151-106">In [!INCLUDE[ssDE](../includes/ssde-md.md)] Tuning Advisor, use the **Select Workload Table** dialog box to select a database table that contains [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace information to use as a tuning workload, or to preview the table contents before starting tuning analysis.</span></span>  
  
## <a name="options"></a><span data-ttu-id="18151-107">옵션</span><span class="sxs-lookup"><span data-stu-id="18151-107">Options</span></span>  
 <span data-ttu-id="18151-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="18151-108">**SQL Server**</span></span>  
 <span data-ttu-id="18151-109">현재 연결된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="18151-109">Specifies the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] currently connected.</span></span> <span data-ttu-id="18151-110">이 필드는 자동으로 채워지며 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="18151-110">This field is populated automatically and cannot be updated.</span></span>  
  
 <span data-ttu-id="18151-111">**Database**</span><span class="sxs-lookup"><span data-stu-id="18151-111">**Database**</span></span>  
 <span data-ttu-id="18151-112">추적 테이블이 있는 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="18151-112">Specify the database where the trace table is located.</span></span>  
  
 <span data-ttu-id="18151-113">**소유자**</span><span class="sxs-lookup"><span data-stu-id="18151-113">**Owner**</span></span>  
 <span data-ttu-id="18151-114">Specifies the owner of the trace table.</span><span class="sxs-lookup"><span data-stu-id="18151-114">Specifies the owner of the trace table.</span></span> <span data-ttu-id="18151-115">이 필드에는 **dbo**가 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="18151-115">This field is populated automatically as **dbo**.</span></span>  
  
 <span data-ttu-id="18151-116">**테이블**</span><span class="sxs-lookup"><span data-stu-id="18151-116">**Table**</span></span>  
 <span data-ttu-id="18151-117">추적을 읽어오는 추적 테이블의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="18151-117">Specify the name of the trace table from which the trace should be read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18151-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="18151-118">See Also</span></span>  
 <span data-ttu-id="18151-119">[테이블에 추적 결과 저장&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="18151-119">[Save Trace Results to a Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="18151-120">[SQL Server Profiler 템플릿 및 권한](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="18151-120">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="18151-121">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="18151-121">Database Engine Tuning Advisor</span></span>](../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
