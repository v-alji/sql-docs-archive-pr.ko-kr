---
title: 오류 로그 모니터링 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server]
- database performance [SQL Server], errors
- Windows application logs [SQL Server]
- monitoring performance [SQL Server], errors
- server performance [SQL Server], errors
- comparing error and application log output
- errors [SQL Server], logs
- tuning databases [SQL Server], errors
- database monitoring [SQL Server], errors
- SQL Server error log
- logs [SQL Server], SQL Server error logs
- error logs [SQL Server]
- logs [SQL Server], Windows application logs
ms.assetid: e250336b-0695-44f6-a42f-23222f94e377
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2a47891599dbe735bd437f5239c73bfd34c422ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650335"
---
# <a name="monitoring-the-error-logs"></a><span data-ttu-id="6f66b-102">오류 로그 모니터링</span><span class="sxs-lookup"><span data-stu-id="6f66b-102">Monitoring the Error Logs</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6f66b-103">는 특정 시스템 이벤트와 사용자 정의 이벤트를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 애플리케이션 로그에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="6f66b-103">logs certain system events and user-defined events to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log.</span></span> <span data-ttu-id="6f66b-104">두 가지 로그 모두 모든 기록된 이벤트에 자동으로 타임스탬프를 남깁니다.</span><span class="sxs-lookup"><span data-stu-id="6f66b-104">Both logs automatically timestamp all recorded events.</span></span> <span data-ttu-id="6f66b-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에 있는 정보를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 관련된 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f66b-105">Use the information in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to troubleshoot problems related to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6f66b-106">Windows 애플리케이션 로그에서 Windows 운영 체제 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 발생하는 이벤트의 전체적인 모습을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f66b-106">The Windows application log provides an overall picture of events that occur on the Windows operating system, as well as events in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="6f66b-107">Windows 이벤트 뷰어를 사용하여 Windows 애플리케이션 로그를 보고 정보를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f66b-107">Use the Windows Event Viewer to view the Windows application log and to filter the information.</span></span> <span data-ttu-id="6f66b-108">예를 들어 정보, 경고, 오류, 성공 감사 및 실패 감사와 같은 이벤트들을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f66b-108">For example, you can filter events, such as information, warning, error, success audit, and failure audit.</span></span>  
  
## <a name="comparing-error-and-application-log-output"></a><span data-ttu-id="6f66b-109">오류 및 애플리케이션 로그 출력 비교</span><span class="sxs-lookup"><span data-stu-id="6f66b-109">Comparing Error and Application Log Output</span></span>  
 <span data-ttu-id="6f66b-110">문제의 원인을 확인하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그와 Windows 애플리케이션 로그를 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f66b-110">You can use both the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and the Windows application log to identify the cause of problems.</span></span> <span data-ttu-id="6f66b-111">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그를 모니터링할 때 원인을 알 수 없는 오류 메시지가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f66b-111">For example, while monitoring the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, you may encounter error messages that do not contain cause information.</span></span> <span data-ttu-id="6f66b-112">이 경우 두 로그 간의 이벤트에 대한 날짜와 시간을 비교하면 가능한 원인 목록을 좁혀 갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f66b-112">By comparing the dates and times for events between these logs, you can narrow the list of probable causes.</span></span> <span data-ttu-id="6f66b-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 로그 파일 뷰어를 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 및 Windows 로그를 단일 목록으로 통합할 수 있어 관련된 서버 이벤트와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이벤트를 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f66b-113">The [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Log File Viewer lets you integrate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, and the Windows logs into a single list, making it easy to understand related server events and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events.</span></span> <span data-ttu-id="6f66b-114">자세한 내용은 SQL Server 온라인 설명서의 "로그 파일 뷰어" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6f66b-114">For more information, see the topic "Log File Viewer" in SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f66b-115">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="6f66b-115">In This Section</span></span>  
  
|<span data-ttu-id="6f66b-116">항목</span><span class="sxs-lookup"><span data-stu-id="6f66b-116">Topic</span></span>|<span data-ttu-id="6f66b-117">Description</span><span class="sxs-lookup"><span data-stu-id="6f66b-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6f66b-118">SQL Server 오류 로그 보기</span><span class="sxs-lookup"><span data-stu-id="6f66b-118">Viewing the SQL Server Error Log</span></span>](../../../2014/tools/configuration-manager/viewing-the-sql-server-error-log.md)|<span data-ttu-id="6f66b-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그 및 이 로그를 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6f66b-119">Contains information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and how to view it.</span></span>|  
|[<span data-ttu-id="6f66b-120">Windows 애플리케이션 로그 보기</span><span class="sxs-lookup"><span data-stu-id="6f66b-120">Viewing the Windows Application Log</span></span>](viewing-the-windows-application-log.md)|<span data-ttu-id="6f66b-121">Windows 애플리케이션 로그 및 이 로그를 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6f66b-121">Contains information about the Windows application log and how to view it.</span></span>|  
  
  
