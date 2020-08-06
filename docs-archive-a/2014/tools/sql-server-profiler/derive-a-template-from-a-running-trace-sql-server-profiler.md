---
title: 실행 중인 추적으로부터 템플릿 파생(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
ms.assetid: 25a3b845-affb-4b2a-a382-198a4bdd9ad1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72744ce942cc49038129cf6064349e23c3e9a41d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727571"
---
# <a name="derive-a-template-from-a-running-trace-sql-server-profiler"></a><span data-ttu-id="71e17-102">실행 중인 추적으로부터 템플릿 파생(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="71e17-102">Derive a Template from a Running Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="71e17-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 실행 중인 기존 추적에서 추적 템플릿을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="71e17-103">This topic describes how to create a trace template from an existing trace while it is running by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-derive-a-template-from-a-running-trace"></a><span data-ttu-id="71e17-104">실행 중인 추적에서 템플릿을 생성하려면</span><span class="sxs-lookup"><span data-stu-id="71e17-104">To derive a template from a running trace</span></span>  
  
1.  <span data-ttu-id="71e17-105">필요한 경우 추적이 포함된 창으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="71e17-105">If necessary, switch to the window that contains the trace.</span></span>  
  
2.  <span data-ttu-id="71e17-106">**파일** 메뉴에서 **다른 이름으로 저장**을 가리킨 다음 **추적 템플릿**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71e17-106">On the **File** menu, point to **Save As**, and then click **Trace Template**.</span></span>  
  
3.  <span data-ttu-id="71e17-107">이름을 입력하거나 목록에서 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71e17-107">Type a name or select one from the list.</span></span> <span data-ttu-id="71e17-108">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71e17-108">Click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71e17-109">기존 템플릿 파일을 선택하면 파일을 덮어쓸 것인지를 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="71e17-109">If you select an existing template file, you are asked if you want to overwrite the file.</span></span> <span data-ttu-id="71e17-110">사용자가 정의한 템플릿만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71e17-110">You can only select a user-defined template.</span></span> <span data-ttu-id="71e17-111">미리 정의된 시스템 추적 템플릿은 덮어쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="71e17-111">Predefined system trace templates cannot be overwritten.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e17-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71e17-112">See Also</span></span>  
 <span data-ttu-id="71e17-113">[SQL Server Profiler 템플릿 및 권한](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="71e17-113">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 <span data-ttu-id="71e17-114">[추적 템플릿 만들기&#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="71e17-114">[Create a Trace Template &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="71e17-115">[추적 템플릿 수정&#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="71e17-115">[Modify a Trace Template &#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="71e17-116">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="71e17-116">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
