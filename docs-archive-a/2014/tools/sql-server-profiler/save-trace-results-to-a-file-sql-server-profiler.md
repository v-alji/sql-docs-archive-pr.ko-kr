---
title: 추적 결과를 파일에 저장(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: ac528747-0c19-4f3d-96f5-44c762a4abed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9644751cda3689cf7b7cb00ec25310bc700ca1c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737221"
---
# <a name="save-trace-results-to-a-file-sql-server-profiler"></a><span data-ttu-id="44da9-102">추적 결과를 파일에 저장(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="44da9-102">Save Trace Results to a File (SQL Server Profiler)</span></span>
  <span data-ttu-id="44da9-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 추적 결과를 파일에 저장하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-103">This topic describes how to save trace results to a file by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-save-trace-results-to-a-file"></a><span data-ttu-id="44da9-104">파일에 추적 결과를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="44da9-104">To save trace results to a file</span></span>  
  
1.  <span data-ttu-id="44da9-105">**파일** 메뉴에서 **새 추적**을 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="44da9-106">**추적 속성**대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="44da9-107">**연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="44da9-108">이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="44da9-109">**추적 이름** 입력란에 추적의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="44da9-110">**파일에 저장** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-110">Select the **Save to file** check box.</span></span>  
  
     <span data-ttu-id="44da9-111">**다른 이름으로 저장**대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-111">The **Save As**dialog box appears.</span></span>  
  
4.  <span data-ttu-id="44da9-112">**다른 이름으로 저장**대화 상자에 경로와 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-112">Specify a path and filename in the **Save As**dialog box.</span></span> <span data-ttu-id="44da9-113">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-113">Click **Save.**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="44da9-114">SQL Server 서비스는 지정된 디렉터리에 있는 파일에 대한 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-114">Ensure that the SQL Server service has sufficient permissions to write to a file in the directory specified.</span></span>  
  
5.  <span data-ttu-id="44da9-115">**추적 속성** 대화 상자에서 **최대 파일 크기 설정(MB)** 입력란에 최대 파일 크기를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-115">In the **Trace Properties** dialog box, enter the maximum file size in the **Set maximum file size (MB)** text box.</span></span> <span data-ttu-id="44da9-116">기본값은 5MB입니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-116">The default value is 5 megabytes (MB).</span></span>  
  
6.  <span data-ttu-id="44da9-117">필요에 따라 다음 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-117">Optionally, specify the following options:</span></span>  
  
    -   <span data-ttu-id="44da9-118">최대 파일 크기에 도달했을 때 **가 추적 데이터용으로 새 파일을 만들도록 하려면** 파일 롤오버 사용 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-118">Select the **Enable file rollover** check box to have [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] create new files for trace data once the maximum file size is reached.</span></span> <span data-ttu-id="44da9-119">이 옵션은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-119">This option is selected by default.</span></span>  
  
    -   <span data-ttu-id="44da9-120">서버가 각 추적 이벤트를 기록하도록 하려면 **서버에서 추적 데이터 처리** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-120">Select the **Server processes trace data** check box to ensure that the server records each trace event.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="44da9-121">**서버에서 추적 데이터 처리**가 선택되지 않은 경우 이벤트 기록으로 인해 성능이 크게 저하되면 서버는 이벤트를 기록하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44da9-121">When **Server processes trace data**is cleared, the server does not record events if recording events significantly degrades performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44da9-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44da9-122">See Also</span></span>  
 [<span data-ttu-id="44da9-123">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="44da9-123">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
