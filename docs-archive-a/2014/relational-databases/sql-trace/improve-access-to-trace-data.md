---
title: 추적 데이터에 대한 액세스 향상 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], space
- SQL Server Profiler, space
- space [SQL Server], SQL Server Profiler
ms.assetid: c260c000-fd53-4831-993f-df6894f3228b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60e01ad04ddd9f7fe6d858c399abb552716f2bea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730295"
---
# <a name="improve-access-to-trace-data"></a><span data-ttu-id="84ad4-102">추적 데이터에 대한 액세스 향상</span><span class="sxs-lookup"><span data-stu-id="84ad4-102">Improve Access to Trace Data</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="84ad4-103">는 추적 데이터에 대한 액세스를 향상시키기 위해 **temp** 디렉터리의 공간을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="84ad4-103">uses space in the **temp** directory to improve access to trace data.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="84ad4-104">에는 적어도 10MB의 사용 가능한 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="84ad4-104">requires at least 10 megabytes (MB) of free space.</span></span> <span data-ttu-id="84ad4-105">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하는 동안 여유 공간이 10MB 이하로 내려가면 모든 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 기능이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="84ad4-105">If free space drops below 10 MB while you are using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] functions stop.</span></span>  
  
 <span data-ttu-id="84ad4-106">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 에서 **temp** 디렉터리의 공간을 사용할 경우 이 공간 사용으로 인해 **temp** 디렉터리가 급격하게 커질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84ad4-106">When [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] uses space in the **temp** directory, this space usage may cause the **temp** directory to grow rapidly.</span></span> <span data-ttu-id="84ad4-107">TEMP 환경 변수의 값을 변경하여 **temp** 디렉터리를 시스템 드라이브가 아닌 드라이브에 두면 파일 증가 문제를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84ad4-107">To avoid file-growth problems, you can place the **temp** directory on a drive that is not a system drive by changing the value for the TEMP environment variable.</span></span>  
  
 <span data-ttu-id="84ad4-108">다음 절차에서는 대부분의 Microsoft Windows 운영 체제에서 TEMP 환경 변수의 값을 변경하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84ad4-108">The following procedure describes how to change the value for the TEMP environment variable in most Microsoft Windows operating systems.</span></span> <span data-ttu-id="84ad4-109">환경 변수를 설정하는 방법은 Windows 운영 체제 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="84ad4-109">For more information about setting environment variables, see your Windows operating system documentation.</span></span>  
  
### <a name="to-change-the-temp-environment-variable-in-windows-operating-systems"></a><span data-ttu-id="84ad4-110">Windows 운영 체제에서 TEMP 환경 변수를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="84ad4-110">To change the TEMP environment variable in Windows operating systems</span></span>  
  
1.  <span data-ttu-id="84ad4-111">**시작** 메뉴에서 **제어판**을 선택하고 **시스템**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84ad4-111">On the **Start** menu, choose **Control Panel**, and then click **System**.</span></span>  
  
2.  <span data-ttu-id="84ad4-112">**시스템 속성** 대화 상자에서 **고급** 탭을 클릭한 다음 **환경 변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84ad4-112">In the **System Properties** dialog box, click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
3.  <span data-ttu-id="84ad4-113">**시스템 변수**목록을 아래로 스크롤하여 **TEMP** 변수에 해당하는 행을 선택하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84ad4-113">Scroll down the list of **System Variables**, select the row that corresponds to the **TEMP** variable, and click **Edit**.</span></span>  
  
4.  <span data-ttu-id="84ad4-114">**시스템 변수 편집** 대화 상자에서 **temp** 디렉터리를 두려는 드라이브와 디렉터리의 경로 및 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="84ad4-114">In the **Edit System Variable** dialog box, enter the path and name of the drive and directory where you want the **temp** directory to be located.</span></span>  
  
5.  <span data-ttu-id="84ad4-115">**확인** 을 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="84ad4-115">Click **OK** to save the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ad4-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="84ad4-116">See Also</span></span>  
 <span data-ttu-id="84ad4-117">[SQL Server Profiler 시작](../../tools/sql-server-profiler/start-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="84ad4-117">[Start SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="84ad4-118">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="84ad4-118">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
