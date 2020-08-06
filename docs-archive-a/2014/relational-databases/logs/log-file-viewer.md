---
title: 로그 파일 뷰어 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer
ms.assetid: a4ea7fc8-1cb2-4c98-bc86-8991c5e748b2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5139a32838070b817fce3bccf22b9fe08b5012e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649534"
---
# <a name="log-file-viewer"></a><span data-ttu-id="1e58e-102">로그 파일 뷰어</span><span class="sxs-lookup"><span data-stu-id="1e58e-102">Log File Viewer</span></span>
  <span data-ttu-id="1e58e-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 의 로그 파일 뷰어를 사용하여 로그 파일에 기록되는 오류 및 이벤트에 대한 정보에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e58e-103">Log File Viewer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is used to access information about errors and events that are captured in log files.</span></span>  
  
## <a name="benefits-of-using-log-file-viewer"></a><span data-ttu-id="1e58e-104">로그 파일 뷰어 사용의 이점</span><span class="sxs-lookup"><span data-stu-id="1e58e-104">Benefits of using Log File Viewer</span></span>  
 <span data-ttu-id="1e58e-105">대상 인스턴스가 오프라인이거나 시작할 수 없는 경우 로컬 또는 원격 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그 파일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e58e-105">You can view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files from a local or remote instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when the target instance is offline or cannot start.</span></span> <span data-ttu-id="1e58e-106">등록된 서버에서 오프라인 로그 파일에 액세스하거나 WMI 및 WQL(WMI Query Language) 쿼리를 통해 프로그래밍 방식으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e58e-106">You can access the offline log files from Registered Servers, or programmatically through WMI and WQL (WMI Query Language) queries.</span></span> <span data-ttu-id="1e58e-107">자세한 내용은 [오프라인 로그 파일 보기](view-offline-log-files.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e58e-107">For more information, see [View Offline Log Files](view-offline-log-files.md).</span></span> <span data-ttu-id="1e58e-108">다음은 로그 파일 뷰어를 사용하여 액세스할 수 있는 로그 파일 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="1e58e-108">Following are the types of log files you can access using Log File Viewer:</span></span>  
  
-   <span data-ttu-id="1e58e-109">감사 컬렉션</span><span class="sxs-lookup"><span data-stu-id="1e58e-109">Audit Collection</span></span>  
  
-   <span data-ttu-id="1e58e-110">데이터 수집</span><span class="sxs-lookup"><span data-stu-id="1e58e-110">Data Collection</span></span>  
  
-   <span data-ttu-id="1e58e-111">데이터베이스 메일</span><span class="sxs-lookup"><span data-stu-id="1e58e-111">Database Mail</span></span>  
  
-   <span data-ttu-id="1e58e-112">작업 기록</span><span class="sxs-lookup"><span data-stu-id="1e58e-112">Job History</span></span>  
  
-   <span data-ttu-id="1e58e-113">유지 관리 계획</span><span class="sxs-lookup"><span data-stu-id="1e58e-113">Maintenance Plans</span></span>  
  
-   <span data-ttu-id="1e58e-114">원격 유지 관리 계획</span><span class="sxs-lookup"><span data-stu-id="1e58e-114">Remote Maintenance Plans</span></span>  
  
-   <span data-ttu-id="1e58e-115">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1e58e-115">SQL Server</span></span>  
  
-   <span data-ttu-id="1e58e-116">SQL Server 에이전트</span><span class="sxs-lookup"><span data-stu-id="1e58e-116">SQL Server Agent</span></span>  
  
-   <span data-ttu-id="1e58e-117">Windows NT(이벤트 뷰어에서도 액세스할 수 있는 Windows 이벤트)</span><span class="sxs-lookup"><span data-stu-id="1e58e-117">Windows NT (These are Windows events that can also be accessed from Event Viewer.)</span></span>  
  
## <a name="log-file-viewer-tasks"></a><span data-ttu-id="1e58e-118">로그 파일 뷰어 태스크</span><span class="sxs-lookup"><span data-stu-id="1e58e-118">Log File Viewer Tasks</span></span>  
  
|<span data-ttu-id="1e58e-119">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="1e58e-119">Task Description</span></span>|<span data-ttu-id="1e58e-120">항목</span><span class="sxs-lookup"><span data-stu-id="1e58e-120">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="1e58e-121">보려는 정보에 따라 로그 파일 뷰어를 여는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1e58e-121">Describes how to open Log File Viewer depending on the information that you want to view.</span></span>|[<span data-ttu-id="1e58e-122">로그 파일 뷰어 열기</span><span class="sxs-lookup"><span data-stu-id="1e58e-122">Open Log File Viewer</span></span>](open-log-file-viewer.md)|  
|<span data-ttu-id="1e58e-123">등록된 서버를 통해 오프라인 로그 파일을 보는 방법과 WMI 사용 권한을 확인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1e58e-123">Describes how to view offline log files through registered servers and how to verify WMI permissions.</span></span>|[<span data-ttu-id="1e58e-124">오프라인 로그 파일 보기</span><span class="sxs-lookup"><span data-stu-id="1e58e-124">View Offline Log Files</span></span>](view-offline-log-files.md)|  
|<span data-ttu-id="1e58e-125">로그 파일 뷰어 F1 도움말을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1e58e-125">Provides Log File Viewer F1 Help.</span></span>|[<span data-ttu-id="1e58e-126">로그 파일 뷰어 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="1e58e-126">Log File Viewer F1 Help</span></span>](log-file-viewer-f1-help.md)|  
  
## <a name="see-also"></a><span data-ttu-id="1e58e-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e58e-127">See Also</span></span>  
 <span data-ttu-id="1e58e-128">[SQL Server Audit&#40;데이터베이스 엔진&#41;](../security/auditing/sql-server-audit-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="1e58e-128">[SQL Server Audit &#40;Database Engine&#41;](../security/auditing/sql-server-audit-database-engine.md) </span></span>  
 [<span data-ttu-id="1e58e-129">SQL Server 에이전트 오류 로그</span><span class="sxs-lookup"><span data-stu-id="1e58e-129">SQL Server Agent Error Log</span></span>](../../ssms/agent/sql-server-agent-error-log.md)  
  
  
