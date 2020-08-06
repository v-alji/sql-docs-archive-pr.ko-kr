---
title: 교착 상태 파일 열기, 보기 및 인쇄(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 08bacd7a99e45e10163216c69057b167088441ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652781"
---
# <a name="open-view-and-print-a-deadlock-file-sql-server-management-studio"></a><span data-ttu-id="66d70-102">교착 상태 파일 열기, 보기 및 인쇄(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="66d70-102">Open, View, and Print a Deadlock File (SQL Server Management Studio)</span></span>
  <span data-ttu-id="66d70-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 에서 교착 상태가 생성되면 교착 상태 정보를 캡처하여 파일에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d70-103">When [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] generates a deadlock, you can capture and save the deadlock information to a file.</span></span> <span data-ttu-id="66d70-104">교착 상태 파일을 저장한 다음 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 해당 파일을 열어서 보거나 인쇄할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66d70-104">After you have saved the deadlock file, you can open it in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to view or print.</span></span>  
  
### <a name="to-open-and-view-a-deadlock-file"></a><span data-ttu-id="66d70-105">교착 상태 파일을 열고 보려면</span><span class="sxs-lookup"><span data-stu-id="66d70-105">To open and view a deadlock file</span></span>  
  
1.  <span data-ttu-id="66d70-106">의 **파일** 메뉴에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **열기**를 가리킨 다음 **파일**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="66d70-106">On the **File** menu in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="66d70-107">**파일 열기** 대화 상자의 **파일 유형** 확인란에서 .xdl 파일 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66d70-107">In the **Open File** dialog box, select the .xdl file type in the **Files of type** box.</span></span> <span data-ttu-id="66d70-108">교착 상태 파일만 필터링한 목록이 남아 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="66d70-108">You will now have a filtered list of only deadlock files.</span></span>  
  
### <a name="to-print-a-deadlock-file"></a><span data-ttu-id="66d70-109">교착 상태 파일을 인쇄하려면</span><span class="sxs-lookup"><span data-stu-id="66d70-109">To print a deadlock file</span></span>  
  
1.  <span data-ttu-id="66d70-110">**의** 파일 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]메뉴에서 **열기** 를 가리킨 다음 **파일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66d70-110">On the **File** menu in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], point to **Open,** and then click **File**.</span></span>  
  
2.  <span data-ttu-id="66d70-111">**파일 열기** 대화 상자의 **파일 유형** 확인란에서 .xdl 파일 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66d70-111">In the **Open File** dialog box, select the .xdl file type in the **Files of type** box.</span></span> <span data-ttu-id="66d70-112">교착 상태 파일만 필터링한 목록이 남아 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="66d70-112">You will now have a filtered list of only deadlock files.</span></span>  
  
3.  <span data-ttu-id="66d70-113">인쇄할 교착 상태 파일을 선택하고 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66d70-113">Select the deadlock file you want to print, and click **Open**.</span></span>  
  
4.  <span data-ttu-id="66d70-114">**파일** 메뉴에서 **인쇄**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66d70-114">On the **File** menu, click **Print.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66d70-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="66d70-115">See Also</span></span>  
 [<span data-ttu-id="66d70-116">교착 상태 그래프 저장&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="66d70-116">Save Deadlock Graphs &#40;SQL Server Profiler&#41;</span></span>](save-deadlock-graphs-sql-server-profiler.md)  
  
  
