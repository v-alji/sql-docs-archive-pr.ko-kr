---
title: 추적 파일에 최대 파일 크기 설정(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- maximum file size for traces
- size [SQL Server], trace files
ms.assetid: e86dc4ce-5aa3-4c0d-acb5-c9e8871ed963
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa990c610f7aa8bf82690c8c201c6643eb712191
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735720"
---
# <a name="set-a-maximum-file-size-for-a-trace-file-sql-server-profiler"></a><span data-ttu-id="34832-102">추적 파일에 최대 파일 크기 설정(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="34832-102">Set a Maximum File Size for a Trace File (SQL Server Profiler)</span></span>
  <span data-ttu-id="34832-103">추적 파일에 최대 파일 크기를 설정하려면 다음 절차를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="34832-103">Use the following procedure to set the maximum file size for a trace file.</span></span>  
  
### <a name="to-set-a-maximum-file-size-for-a-trace-file"></a><span data-ttu-id="34832-104">추적 파일에 최대 파일 크기를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="34832-104">To set a maximum file size for a trace file</span></span>  
  
1.  <span data-ttu-id="34832-105">**파일** 메뉴에서 **새 추적**을 클릭한 다음 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="34832-105">On the **File** menu, click **New Trace**, and then connect to an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="34832-106">**추적 속성**대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="34832-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="34832-107">**연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="34832-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="34832-108">이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="34832-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="34832-109">**추적 이름** 입력란에 추적의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="34832-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="34832-110">**템플릿 이름**목록에서 추적 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34832-110">In the **Template name**list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="34832-111">**파일에 저장**을 선택한 다음 추적 정보를 저장할 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34832-111">Select **Save to file**, and then specify a file to store the trace information.</span></span>  
  
5.  <span data-ttu-id="34832-112">**최대 파일 크기 설정** 입력란에 추적할 최대 파일 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34832-112">In the **Set maximum file size** check box, specify a maximum file size for the trace.</span></span> <span data-ttu-id="34832-113">파일 크기가 이 최대 크기에 도달하면 추적 이벤트는 더 이상 이 파일에 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34832-113">When the file size reaches this maximum, trace events are no longer recorded in this file.</span></span> <span data-ttu-id="34832-114">**파일 롤오버 사용** 을 선택하면(기본값으로 선택됨) 다음이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="34832-114">If you select **Enable file rollover** (which is selected by default),the following occurs:</span></span>  
  
     <span data-ttu-id="34832-115">파일 롤오버 옵션을 사용할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 최대 파일 크기에 도달하면 현재 파일을 닫고 새 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="34832-115">The file rollover option causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to close the current file and create a new file when the maximum file size is reached.</span></span> <span data-ttu-id="34832-116">새 파일의 이름은 이전 파일의 이름과 동일하지만 이름에 순서를 나타내는 정수가 추가됩니다. 예를 들어 원래의 추적 파일 이름이 filename_1.trc라면 다음 추적 파일은 filename_2.trc입니다.</span><span class="sxs-lookup"><span data-stu-id="34832-116">The new file has the same name as the previous file, but an integer is appended to the name to indicate its sequence; for example, if the original trace file is named filename_1.trc, the next trace file is filename_2.trc, and so on.</span></span> <span data-ttu-id="34832-117">새 롤오버 파일에 할당된 이름을 기존 파일이 이미 사용했다면 읽기 전용이 아닌 경우 기존 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="34832-117">If the name assigned to a new rollover file is already used by an existing file, the existing file is overwritten unless it is read-only.</span></span> <span data-ttu-id="34832-118">추적 데이터를 파일로 저장할 때 파일 롤오버 옵션이 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="34832-118">The file rollover option is enabled by default when you are saving trace data to a file.</span></span>  
  
     <span data-ttu-id="34832-119">파일 롤오버 옵션이 설정되어 있으면 추적은 다른 방법으로 중단되기 전까지 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="34832-119">With the file rollover option on, the trace continues until it is stopped by some other means.</span></span> <span data-ttu-id="34832-120">파일 크기 제한에 도달한 후 추적을 중지하려면 파일 롤오버 옵션을 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="34832-120">To stop the trace after you have reached the file size limit, disable the file rollover option.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="34832-121">FAT32 파일 시스템에서 파일의 크기는 4GB 미만으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="34832-121">The FAT32 file system limits files to slightly less than 4 gigabytes (GB).</span></span> <span data-ttu-id="34832-122">추적 파일의 크기가 이 크기에 도달하면 추적이 실패하고 "디스크 공간이 부족합니다"라는 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="34832-122">When the trace file reaches that size, the trace fails with the error "Not enough disk space."</span></span> <span data-ttu-id="34832-123">더 큰 파일을 만들려면 NTFS 파일 시스템을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="34832-123">To create larger files, use the NTFS file system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34832-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34832-124">See Also</span></span>  
 [<span data-ttu-id="34832-125">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="34832-125">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
