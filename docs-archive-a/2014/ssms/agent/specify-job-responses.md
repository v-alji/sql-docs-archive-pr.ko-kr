---
title: 작업 응답 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], responses
- SQL Server Agent jobs, responses
- actions [SQL Server Agent jobs]
- responding to jobs
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
author: stevestein
ms.author: sstein
ms.openlocfilehash: d41c5e1552a1ff16343bdb2c4e9feaafb51c5783
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727895"
---
# <a name="specify-job-responses"></a><span data-ttu-id="c47b1-102">작업 응답 지정</span><span class="sxs-lookup"><span data-stu-id="c47b1-102">Specify Job Responses</span></span>
  <span data-ttu-id="c47b1-103">작업 응답은 작업이 완료된 후 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 수행할 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c47b1-103">Job responses specify actions that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service will take after a job completes.</span></span> <span data-ttu-id="c47b1-104">작업 응답은 데이터베이스 관리자에게 작업 완료 시점과 작업 실행 간격을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="c47b1-104">Job responses ensure that database administrators know when jobs complete and how frequently they run.</span></span> <span data-ttu-id="c47b1-105">일반적인 작업 응답은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c47b1-105">Typical job responses include:</span></span>  
  
-   <span data-ttu-id="c47b1-106">전자 메일, 전자 호출 또는 **net send** 메시지 등으로 운영자에게 알림</span><span class="sxs-lookup"><span data-stu-id="c47b1-106">Notifying the operator by using e-mail, electronic paging, or a **net send** message.</span></span>  
  
     <span data-ttu-id="c47b1-107">운영자가 추가 작업 동작을 실행해야 할 경우 이 작업 응답 중 하나를 사용.</span><span class="sxs-lookup"><span data-stu-id="c47b1-107">Use one of these job responses if the operator must perform a follow-up action.</span></span> <span data-ttu-id="c47b1-108">예를 들어 백업 작업이 성공적으로 완료될 경우 운영자는 백업 테이프를 빼낸 다음 안전한 곳에 저장하도록 알림을 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c47b1-108">For example, if a backup job completes successfully, the operator must be notified to remove the backup tape and store it in a safe location.</span></span>  
  
-   <span data-ttu-id="c47b1-109">이벤트 메시지를 Windows 애플리케이션 로그에 씀</span><span class="sxs-lookup"><span data-stu-id="c47b1-109">Writing an event message to the Windows application log.</span></span>  
  
     <span data-ttu-id="c47b1-110">이 응답은 실패한 작업에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c47b1-110">You can use this response only for failed jobs.</span></span>  
  
-   <span data-ttu-id="c47b1-111">작업을 자동 삭제함</span><span class="sxs-lookup"><span data-stu-id="c47b1-111">Automatically deleting the job.</span></span>  
  
     <span data-ttu-id="c47b1-112">이 작업을 반환할 필요가 없을 경우에는 이 작업 응답을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c47b1-112">Use this job response if you are certain that you do not need to rerun this job.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c47b1-113">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c47b1-113">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c47b1-114">**설명**</span><span class="sxs-lookup"><span data-stu-id="c47b1-114">**Description**</span></span>|<span data-ttu-id="c47b1-115">**항목**</span><span class="sxs-lookup"><span data-stu-id="c47b1-115">**Topic**</span></span>|  
|<span data-ttu-id="c47b1-116">운영자에게 작업 상태를 알리는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c47b1-116">Describes how to notify an operator of job status.</span></span>|[<span data-ttu-id="c47b1-117">Notify an Operator of Job Status</span><span class="sxs-lookup"><span data-stu-id="c47b1-117">Notify an Operator of Job Status</span></span>](notify-an-operator-of-job-status.md)|  
|<span data-ttu-id="c47b1-118">Windows 애플리케이션 로그에 작업 상태를 기록하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c47b1-118">Describes how to write job status to the Windows application log.</span></span>|[<span data-ttu-id="c47b1-119">Windows 애플리케이션 로그에 작업 상태 쓰기</span><span class="sxs-lookup"><span data-stu-id="c47b1-119">Write the Job Status to the Windows Application Log</span></span>](../../reporting-services/report-server/windows-application-log.md)|  
  
## <a name="see-also"></a><span data-ttu-id="c47b1-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c47b1-120">See Also</span></span>  
 [<span data-ttu-id="c47b1-121">이벤트 모니터링 및 응답</span><span class="sxs-lookup"><span data-stu-id="c47b1-121">Monitor and Respond to Events</span></span>](monitor-and-respond-to-events.md)  
  
  
