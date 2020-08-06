---
title: '작업 속성: 새 작업 (알림 페이지) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
author: stevestein
ms.author: sstein
ms.openlocfilehash: 30eca88943b48bd81bd38e236711d19ee7ec4503
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646797"
---
# <a name="job-properties-new-job-notifications-page"></a><span data-ttu-id="09796-102">작업 속성: 새 작업(알림 페이지)</span><span class="sxs-lookup"><span data-stu-id="09796-102">Job Properties: New Job (Notifications Page)</span></span>
  <span data-ttu-id="09796-103">이 페이지를 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 작업이 완료 되었을 때 수행할 동작을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09796-103">Use this page to set actions for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform when the job completes.</span></span>  
  
## <a name="options"></a><span data-ttu-id="09796-104">옵션</span><span class="sxs-lookup"><span data-stu-id="09796-104">Options</span></span>  
 <span data-ttu-id="09796-105">**주소**</span><span class="sxs-lookup"><span data-stu-id="09796-105">**E-mail**</span></span>  
 <span data-ttu-id="09796-106">작업이 완료되었을 때 전자 메일을 보내려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="09796-106">Select this option to send e-mail when the job completes.</span></span> <span data-ttu-id="09796-107">이 옵션을 선택한 후 알릴 운영자와 **작업 성공 시**, **작업 실패 시**, **작업 완료 시**등 알림을 트리거할 조건을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="09796-107">After selecting this option, choose the operator to notify and the condition that will trigger the notification: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="09796-108">**호출**</span><span class="sxs-lookup"><span data-stu-id="09796-108">**Page**</span></span>  
 <span data-ttu-id="09796-109">작업이 완료되었을 때 운영자의 호출기로 전자 메일을 보내려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="09796-109">Select this option to send e-mail to an operator's pager when the job completes.</span></span> <span data-ttu-id="09796-110">이 옵션을 선택한 후 알릴 운영자와 **작업 성공 시**, **작업 실패 시**, **작업 완료 시**등 알림을 트리거할 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="09796-110">After selecting this option, specify the operator to notify and the condition that will trigger the notification: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="09796-111">**Net Send**</span><span class="sxs-lookup"><span data-stu-id="09796-111">**Net send**</span></span>  
 <span data-ttu-id="09796-112">작업이 완료되었을 때 Net Send를 사용하여 운영자에게 알리려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="09796-112">Select this option to use net send to notify an operator when the job completes.</span></span> <span data-ttu-id="09796-113">이 옵션을 선택한 후 알릴 운영자와 **작업 성공 시**, **작업 실패 시**, **작업 완료 시**등 알림을 트리거할 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="09796-113">After selecting this option, specify the operator to notify and the condition that will trigger the notification: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="09796-114">**Windows 애플리케이션 이벤트 로그에 쓰기**</span><span class="sxs-lookup"><span data-stu-id="09796-114">**Write to the Windows Application event log**</span></span>  
 <span data-ttu-id="09796-115">작업이 완료되었을 때 애플리케이션 이벤트 로그에 항목을 쓰려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="09796-115">Select this option to write an entry in the application event log when the job completes.</span></span> <span data-ttu-id="09796-116">이 옵션을 선택한 후 **작업 성공 시**, **작업 실패 시**, **작업 완료 시**등 항목을 쓰도록 할 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="09796-116">After selecting this option, specify the condition that will cause the entry to be written: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
 <span data-ttu-id="09796-117">**자동으로 작업 삭제**</span><span class="sxs-lookup"><span data-stu-id="09796-117">**Automatically delete job**</span></span>  
 <span data-ttu-id="09796-118">작업이 완료되었을 때 작업을 삭제하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="09796-118">Select this option to delete the job when the job completes.</span></span> <span data-ttu-id="09796-119">이 옵션을 선택한 후 **작업 성공 시**, **작업 실패 시**, **작업 완료 시**등 작업 삭제를 트리거할 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="09796-119">After selecting this option, specify the condition that will trigger deletion of the job: **When the job succeeds**; **When the job fails**; or **When the job completes**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09796-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="09796-120">See Also</span></span>  
 <span data-ttu-id="09796-121">[작업 구현](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="09796-121">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="09796-122">데이터베이스 메일을 사용하도록 SQL Server 에이전트 메일 구성</span><span class="sxs-lookup"><span data-stu-id="09796-122">Configure SQL Server Agent Mail to Use Database Mail</span></span>](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
  
